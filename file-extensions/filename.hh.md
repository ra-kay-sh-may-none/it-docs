# HHMD (.WITH FILE EXTENSION .hh.md) (Hash Hierarchical Markdown) Full Specification
**Version:** 1.2
**Official Extension:** `.hh.md`

HHMD (.WITH FILE EXTENSION .hh.md) is a strictly hierarchical format designed for structured data where every line is a node in a tree.

## 1. Structural Fundamentals
### 1.1 Line Indicators
Every line must begin with a level indicator: `[Hashes][Dot][Space]`.
*   **Indicator Syntax:** The indicator is always `n` hashes followed by a single dot.
*   **Infinite Depth:** There is no limit to the number of levels (Level 4 is `####.`, Level 6 is `######.`, Level N is `n` hashes followed by a dot).

### 1.2 Indentation and Tabs
Indentation must match the hash count exactly to facilitate editor folding.
*   **Rule:** `Tabs = Hashes - 1`.
*   **Example:** Level 1 has 0 tabs, Level 6 has 5 tabs.

### 1.3 Line Termination
*   Every line (except code) must end with `.`, `?`, `!`, or `:`.
*   **Colon Rule:** If a line ends with `:`, the next line **must** be a sub-level (indented further).
*   **Constraint:** If a line is a sub-level, its parent **must** end with `:`.

## 2. Code and Preformatted Blocks
### 2.1 The Fence
*   A code fence consists only of `[Hashes][Dot]` (e.g., `####.`).
*   The fence must have **one more hash** than the parent text level.

### 2.2 Content Indentation
*   Code inside the fences must be indented **one tab deeper** than the fence lines.
*   Formatting rules (punctuation and sentence count) are suspended inside the block.

## 3. Examples
### N-Level Deep Nesting
#. Level 1 Main Topic:
	##. Level 2 Detail:
		###. Level 3 Sub-detail:
			####. Level 4 Specifics:
				#####. Level 5 Nuance:
					######. Level 6 Final Point.

### Python Code and Docstring
#. Programming Guide:
	##. Python Function:
		###. Example with docstring:
			####.
				def example():
					"""
					This is a multi-line docstring.
					####. This hash-dot does not break the format.
					The +2 indentation protects this text.
					"""
					return True
			####.

### Incorrect Usage (Avoid these)
#. Missing punctuation at the end
# No dot after hashes.
	##. This has a tab but the parent above has no colon:
