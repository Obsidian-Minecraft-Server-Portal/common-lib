# Obsidian Server Portal Library

This Rust library serves as a utility for the [Obsidian Server Portal](https://github.com/your-repo-link), a Minecraft server panel. The library provides support for path transformations and related functionalities.

## Features

- **Path Transformations**: Includes utilities to manipulate file paths with traits for normalization, conversion to absolute paths, and conversion to relative paths based on the current executable's location.
- **Git Dependency**: This library can only be added as a dependency via its Git repository.

## Getting Started

### Adding the Library to Your Project

To add this library as a dependency, include the following in your `Cargo.toml`:

```toml
[dependencies]
obsidian_server_portal_lib = { git = "https://github.com/your-repo-link" }
```

Make sure to replace `https://github.com/your-repo-link` with the actual URL to your Git repository.

### Usage Example

Use the `TransformPath` trait to perform operations on file paths. Here's a quick example:

```rust
use obsidian_server_portal_lib::traits::TransformPath;
use std::path::PathBuf;

fn main() -> Result<(), Box<dyn std::error::Error>> {
    let relative_path = PathBuf::from("relative/path/to/file");
    
    // Normalize the path
    let normalized_path = relative_path.normalize();
    println!("Normalized Path: {:?}", normalized_path);
    
    // Convert to absolute path
    let absolute_path = relative_path.to_absolute()?;
    println!("Absolute Path: {:?}", absolute_path);
    
    // Convert to relative path
    let relative_back = absolute_path.to_relative()?;
    println!("Relative Path: {:?}", relative_back);
    
    Ok(())
}
```

## Library Structure

The code is organized as follows:

- `traits.rs`: Defines the `TransformPath` trait and its implementation for `PathBuf`. Features methods for:
    - **normalize**: Resolves and normalizes a file path.
    - **to_absolute**: Converts a relative path into an absolute path based on the directory of the currently running executable.
    - **to_relative**: Converts an absolute path into a relative path.

- `lib.rs`: The main module entry point that exposes the `traits` module externally.

## Contributing

Contributions are welcome! If you'd like to add features or report bugs, feel free to open issues and pull requests on the GitHub repository.

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Write your code and tests.
4. Submit a pull request.

## License

This library is open-source and available under the [LGPL-3.0](LICENSE).

---

### Notes

- This library is designed as a utility for the Obsidian Server Portal and may not cover path transformation needs beyond its intended scope.
- Ensure that the library is linked as a Git dependency in your project as it is not published on [crates.io](https://crates.io).
