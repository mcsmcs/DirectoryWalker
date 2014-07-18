DirectoryWalker
===============

An event emitter that walks a specified directory and emits 'file' and 'directory' events.

	// Require the module
    var DirectoryWalker = require('./DirectoryWalker');
    
    // Create a new walker
    var walker = new DirectoryWalker()
	
	// Add your listeners (events: 'file', 'directory', 'done')
	walker.on('file', function(file){ /* do something with the file here */ });
	walker.on('done', function(results){ /* save/do some processing of the files & directories */ });

	// Execute the directory walk
	walker.walk('../some/folder/');



Done Event emits a results object with 2 arrays: directories, files

	walker.on('done', function(results){ console.log(results); });
	
	//	{
	//		directories: [],
	//		files: []
	//	}


File event emits a String containing the (relative) path and filename for each file in the walked path

	walker.on('file', function(file){ console.log(file); });	//	'../path/to/some/file.txt'


Directory event emits a String with the (relative) path for each directory in the walked path
    
    walker.on('directory', function(directory){ console.log(directory); });	// '../my/folder'
