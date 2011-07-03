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

See http://gopkgdoc.appspot.com/pkg/github.com/crazy2be/iomod for a full function reference.