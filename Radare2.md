# Radare2

The following are s set of Radare2 commanads that you may find useful in analyse executables.

## Baasic Radare2 Commands

load without any analysis (file header at offset 0x0): `r2 -n /path/to/file`

  - analyze all: `aa`
  - show sections: `iS`
  - list functions: `afl`
  - list imports: `ii`
  - list entrypoints: `ie`
  - seek to function: `s sym.main`

## project management 

  - open project: `Po <name>`
  - save project: `Ps <name>`
  - edit project notes: `Pn -`

## inspecting a function

  - show basic block disassembly: `pdb`
  - show function disassembly: `pdf`
  - show function arguments: `afa`
  - show function variables: `afv`
  - rename function variable: `afvn`
  - set function variable type: `afvt`
  - add/analyze function: `af`

## comments:
by default, these get displayed in disassembly listings to the right of a line.
disable them in V visual mode using ' (single quote).

multiline comments are not rendered handled well. they don't look pretty.

  - add comment (using editor): `CC!`
    - note: multiline comments are not formatted nicely
  - append comment: `CC <text>`
  - overwrite comment: `CCu <text>`
  - show comment: `CC.`
  - show comment in this function: `CCf`

## visual mode

  - enter visual mode: `V`
  - select function, variable, xref: `v`
  - quick command/seek: `_ <search string>`
  - custom quick command list: `??`
    - you can update the list of commands shown here by changing `$R2HOME/hud`.
    - ref: http://radare.today/posts/visual-mode/
  - show cursor: `c`
  - set function name: `d`
  - add comment: `;`
  - remove comment: `;-`
  
"flag" means give something a type. like function or symbol.

## graph mode

graph mode is not visual mode!

  - enter graph modes: `VV`
  - cycle types of graphs:
    - forward: `p`
    - backwards: `P`

  - types of graphs:
      - graph view
      - graph view + opcode bytes
      - esil
      - esil + comments
      - overview

  - seek to function: `g<identifier>`
  - undo seek: `u`
  - define new function at cursor: `df`
  - rename function at cursor: `dr`  
  - show comments: `'`
  - add comment: `/`
  - add comment (complex): `:CC!`
  - select bb: `???`
  - seek to next bb: `tab`
  - seek to previous bb: `TAB`
  - if bb has conditional branch:
    - seek to True target: `t`
    - seek to False target: `f`

## pipe,grep,etc ###

  - exec multiple cmd: `;`
  - pipeline cmd: `|`
  - run shell cmd: '!' , and give output back to r2 buffer: '!!'
  - grep:
    - `<cmd>~<string>` grep string from command output 
    - `<cmd>~[n]` grep also the 'n' column
    - `<cmd>~:n` grep also the 'n' row


## analysis, assembly, memory ###

  - analyze functions: `af`
  - analyze stack: `ad@rsp` or `ad@esp`
  - search for opcode: `/a`
  - search for rop/jop/etc: `/R`
  - search for bytes: `/x `
  - get offset for the actual seek point address: `?p`
    
## Contact Details

For further information and questions please contact Dr Andrew Blyth, PhD. ablyth@merimetso.net
