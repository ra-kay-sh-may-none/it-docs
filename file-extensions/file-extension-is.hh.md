#. HHMD Standard Version 1.0 (Hash Hierarchical Markdown):
	##. Core Structural Rules:
		###. Line Initialization:
			####. Every line must start with a level indicator consisting of hashes and a dot.
			####. The number of hashes represents the depth level.
			####. Level 1 starts with #. and has zero leading tabs.
			####. Each subsequent level adds exactly one # and one Tab character.
		###. Line Termination:
			####. Every line must end with a punctuation mark such as ., ?, !, or :.
			####. A line ending with a colon : is a Parent Heading and requires a sub-level.
			####. A line that is a sub-level requires its parent line to end with a colon :.
		###. Content Density:
			####. A single line can contain a maximum of two sentences.
			####. If a line has two sentences, the first must end with punctuation followed by a space.
			####. Large paragraphs are strictly forbidden.
		###. Spacing and Layout:
			####. One empty line is allowed between Level 1 blocks only.
			####. Empty lines are forbidden anywhere else in the document.
	##. Formatting and Media:
		###. Text Styling:
			####. Bold, italics, underlines, and strikethroughs are not supported.
			####. Hyperlinks must be enclosed in parentheses like (https://example.com).
		###. Code and Preformatted Blocks:
			####. Blocks are fenced by a line containing only hashes and a dot.
			####. The fence must have one more # than its container text.
			####. All content inside the block must be indented one additional tab from the fence.
			####. Inside the block, sentence counts and line-ending rules are suspended.
	##. Examples of Correct Usage:
		###. Standard Nested Text:
			####.
				#. Level 1 Title:
					##. This is a sentence. This is the second sentence.
					##. Is this a question?
					##. Sub-heading:
						###. Supporting detail.
			####.
		###. Code Block Implementation:
			####.
				#. Programming Guide:
					##. Python Example:
						###.
							def hello():
								print("Hello World")
						###.
			####.
	##. Examples of Incorrect Usage:
		###. Invalid Indentation or Punctuation:
			####.
				#. No punctuation at the end
				##. Missing colon for sub-level
					###. This level is orphaned.
				#. Too many sentences. This is one. This is two. This is three.
			####.
		###. Invalid Code Fencing:
			####.
				#. Coding:
					##.
						print("The fence above is missing a dot.")
					##.
			####.
	##. Python Function Example:
		###. This line ends with a colon to indicate the code block is a child:
			####.
				def greet(name):
					# This content is indented +2 tabs from the parent
					# Spaces and line breaks are preserved here
					print("Hello, " + name + "!")
			####.
		###. Creating a Docstring:
			####. The following code uses triple quotes and internal hashes:
				#####.
					def example_function():
						"""
						This is a multi-line docstring.
						#####. This hash does not break the HHMD format.
						It is treated as raw text because it is inside the block.
						"""
						return True
				#####.
	##. The block above is safe because of the +2 indentation.
