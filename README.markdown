I/O Modification Libary
=======================

Provides utility functions for modification and tracking of byte steams (io.Readers and io.Writers)

Install:

	goinstall github.com/crazy2be/iomod

Import:

	import "github.com/crazy2be/iomod"

Use:

	countReader := iomod.NewReadCounter(reader)

	someCallThatReadsFromReader(countReader)

	fmt.Println(countReader.Count)

Functions
---------

	type ReadCounter struct {
			Count int
			// contains filtered or unexported fields
	}
ReadCounter allows counting of the number of bytes read from a reader without control of the underlying reader.

### func NewReadCounter(reader io.Reader) (r *ReadCounter)

### func (r *ReadCounter) Read(b []byte) (n int, e os.Error)

	type Replacer struct {
			From  io.Reader
			Start *regexp.Regexp
			End   []byte
	}
Replacer provides a simple way to replace bytes in an incoming stream with any bytes you like. It uses a regexp internally, but it should be noted that regexps that cross Read() boundries will not match both sides of the boundry. For this reason, the longer the pattern, the less likely you are to get accurate results. Only works 100% reliably with single-byte replacements.

### func NewReplacer(From io.Reader, start string, end string) (rep *Replacer)

### func (r *Replacer) Read(p []byte) (n int, err os.Error)
