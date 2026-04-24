#. Set folding strategy for only markdown files
	##. Open settings.json
	##. Add the following lines
		###.
            "files.associations": {
                "*.hh.md": "markdown-hh"
            },
            "[markdown-hh]": {
                "editor.foldingStrategy": "indentation"
            },
		###.