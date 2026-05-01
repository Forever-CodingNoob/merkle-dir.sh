# merkle-dir.sh

`merkle-dir.sh` creates a Merkle tree from any directory. Specifically, it
+ create a merkle tree of a given directory,
+ generate an inclusion proof for any file under the directory, and
+ verify inclusion proofs (to prove the integrity of a file).

Our format of merkle tree (as a file) and inclusion proof mainly follows [RFC 9162](https://www.rfc-editor.org/rfc/rfc9162).
More importantly, it's written in Bash!

## Usage
```
merkle-dir.sh - A tool for working with Merkle trees of directories.

Usage:
  merkle-dir.sh <subcommand> [options] [<argument>]
  merkle-dir.sh build <directory> --output <merkle-tree-file>
  merkle-dir.sh gen-proof <path-to-leaf-file> --tree <merkle-tree-file> --output <proof-file>
  merkle-dir.sh verify-proof <path-to-leaf-file> --proof <proof-file> --root <root-hash>

Subcommands:
  build          Construct a Merkle tree from a directory (requires --output).
  gen-proof      Generate a proof for a specific file in the Merkle tree (requires --tree and --output).
  verify-proof   Verify a proof against a Merkle root (requires --proof and --root).

Options:
  -h, --help     Show this help message and exit.
  --output FILE  Specify an output file (required for build and gen-proof).
  --tree FILE    Specify the Merkle tree file (required for gen-proof).
  --proof FILE   Specify the proof file (required for verify-proof).
  --root HASH    Specify the expected Merkle root hash (required for verify-proof).

Examples:
  merkle-dir.sh build dir1 --output dir1.mktree
  merkle-dir.sh gen-proof file1.txt --tree dir1.mktree --output file1.proof
  merkle-dir.sh verify-proof dir1/file1.txt --proof file1.proof --root abc123def456
```

## Similar Projects
+ [merkdir](https://github.com/makew0rld/merkdir) (written in Go)
+ [merkle-dir](https://github.com/juliangruber/merkle-dir) (written in Javascript)

## License
`merkle-dir.sh` is licensed under GNU GPL v3.0.
