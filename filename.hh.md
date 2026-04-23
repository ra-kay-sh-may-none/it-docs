# HHMD (Hash Hierarchical Markdown) Full Specification
**Version:** 1.1  
**Official Extension:** `.hh.md`  

HHMD is a strictly hierarchical, tree-structured plain-text format. Its primary goal is to eliminate large prose paragraphs and enforce a clear, foldable data structure.

## 1. Structural Fundamentals
### 1.1 Line Indicators (The "Indicator")
Every line in an HHMD file must begin with a level indicator composed of hash symbols (`#`), a period (`.`), and a single space.
*   Syntax: [Hashes].[Space][Content]
*   Depth: The number of hashes directly corresponds to the nesting depth.
*   Formatting: Bold, italics, and underlines are forbidden.

### 1.2 Indentation (The "Tab Rule")
Visual indentation must strictly match the hash depth.
*   Level 1 (#.): 0 leading tabs.
*   Level 2 (##.): 1 leading tab.
*   Level 3 (###.): 2 leading tabs.
*   Rule: Every subsequent level adds exactly one hash and one tab.

### 1.3 Line Termination and Hierarchy
*   Mandatory Punctuation: Every line must end in a punctuation mark (typically ., ?, !, or :).
*   The Colon Trigger (:): If a line ends with a colon, it is a Parent Heading. It must be followed by at least one indented sub-level on the next line.
*   Sub-level Requirement: Any line that is indented (Level 2+) must have a parent line above it that ends with a colon.

## 2. Content Constraints
### 2.1 Sentence Density
*   Maximum Sentences: A single line can contain a maximum of two sentences.
*   Spacing: If two sentences share a line, the first must end with punctuation followed by exactly one space.
*   Prose Restriction: Large blocks of text (paragraphs) are strictly forbidden. Content must be broken into separate hierarchical lines.

### 2.2 Layout and Spacing
*   Empty Lines: Exactly one empty line is permitted only between Level 1 (#.) blocks to separate major sections.
*   No Other Gaps: Empty lines are forbidden between nested levels (e.g., between a ##. and ###.).

## 3. Code and Preformatted Blocks
### 3.1 The Code Fence
*   Syntax: A line consisting only of hashes and a dot (e.g., ####.).
*   Logic: The fence must have exactly one more hash than the text level it belongs to.
*   Pairs: Code blocks must be opened and closed by identical fences.

### 3.2 Block Content
*   Indentation: All content inside the block must be indented one additional tab deeper than the fence lines (+2 tabs from the parent text).
*   Rule Suspension: Inside these blocks, the "two-sentence" limit and "mandatory punctuation" rules are suspended.

## 4. Examples
### Correct Example (Basic Structure)
#. Project Overview:
	##. This is a Level 2 sentence. This is the second sentence.
	##. Does this format work? Yes.
	##. Technical Requirements:
		###. Use the latest version of Python (https://python.org).

### Correct Example (Code Block with Docstring)
#. Python Documentation Guide:
	##. Creating a Docstring:
		###. The following code uses triple quotes and internal hashes:
			####.
				def example_function():
					"""
					This is a multi-line docstring.
					####. This hash does not break the HHMD format.
					It is treated as raw text because it is inside the block.
					"""
					return True
			####.

### Incorrect Example (Broken Rules)
#. This line has no punctuation
##. This is a level 2 line but the level 1 above it is missing a colon
	###. Too many sentences here. One. Two. Three. Four.
