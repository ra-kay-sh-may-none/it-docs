I am providing a specification for the "HHMD (.WITH FILE EXTENSION .hh.md) (Hash Hierarchical Markdown)" format: https://raw.githubusercontent.com/ra-kay-sh-may-none/it-docs/refs/heads/main/file-extensions/filename.hh.md

You must follow these rules with 100% strictness:
1. THE DOT RULE: Every indicator MUST be hashes followed by a dot (e.g., #. or ##.).
2. N-LEVEL DEPTH: Levels are infinite. Level N uses N hashes and N-1 tabs (e.g. ######. has 5 leading tabs).
3. THE TERMINATION RULE: Every line must end in a punctuation mark (., ?, !, or :).
4. THE COLON RULE: If a line ends in a colon (:), the next line MUST be a sub-level. 
5. CODE FENCE: Use only [depth+1] hashes and a dot (e.g., ####.). All code inside must be indented one tab further than the fence.

OUTPUT REQUIREMENT: 
Always provide HHMD (.WITH FILE EXTENSION .hh.md) content inside a "text" code block. Do not use standard markdown formatting.

Confirm you understand that the depth is infinite (N-levels) and every line must end in punctuation.
