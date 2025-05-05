# PyGit

A lightweight Git client implementation in Python that re-implements core Git commands in under 500 lines of code. This project demonstrates the fundamental concepts of Git's object model and pack protocol using Python's standard library modules.

## Features

- Core Git functionality including:
  - Repository initialization (`init`)
  - File staging (`add`)
  - Commit creation (`commit`)
  - Status checking (`status`)
  - Diff viewing (`diff`)
  - Remote operations (`push`)
- Implements Git's object model (blobs, trees, commits)
- Handles Git's pack protocol for efficient data transfer
- Uses standard library modules:
  - `struct` for binary data handling
  - `zlib` for compression
  - `hashlib` for SHA-1 hashing

## Requirements

- Python 3.x
- Standard library modules (no external dependencies)

## Usage

### Basic Commands

```bash
# Initialize a new repository
python pygit.py init <repo-name>

# Add files to staging
python pygit.py add <file1> <file2> ...

# Create a commit
python pygit.py commit -m "commit message"

# Check repository status
python pygit.py status

# View changes
python pygit.py diff

# Push changes to remote
python pygit.py push <remote-url>
```

### Environment Variables

The following environment variables can be set in a `.env` file:

- `GIT_AUTHOR_NAME`: Your name
- `GIT_AUTHOR_EMAIL`: Your email
- `GIT_USERNAME`: Remote repository username
- `GIT_PASSWORD`: Remote repository password

## Implementation Details

PyGit implements the core concepts of Git:

1. **Object Model**:
   - Blobs: Store file contents
   - Trees: Represent directory structure
   - Commits: Store metadata and reference to tree

2. **Index**:
   - Tracks staged changes
   - Maintains file metadata

3. **Pack Protocol**:
   - Efficient transfer of objects
   - Delta compression

## Project Structure

```
pygit/
├── pygit.py      # Main implementation
└── .env          # Environment configuration
```

## License

This project is open source and available under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. 
