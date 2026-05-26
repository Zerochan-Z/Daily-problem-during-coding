
---

### Scenario

You have a messy folder with mixed files. You want to:
1. Scan all files
2. Sort them by type (`.csv`, `.py`, `.txt`, etc.)
3. Move them into subfolders

---

### Complete Code

```python
import os
import shutil  # For moving files

# Folder to clean
folder_path = os.path.join(os.getcwd(), "messy_folder")

# Create example messy folder with test files
def create_messy_folder():
    if not os.path.exists(folder_path):
        os.makedirs(folder_path)
    
    # Create some dummy files
    for f in ["data1.csv", "data2.csv", "script.py", "notes.txt", "report.csv", "README.md"]:
        file_path = os.path.join(folder_path, f)
        if not os.path.exists(file_path):
            with open(file_path, 'w') as file:
                file.write(f"# {f} content\n")
    
    print(f"📁 Created messy folder at: {folder_path}")

# Scan and organize files
def organize_folder():

    if not os.path.exists(folder_path):
        print("❌ Folder not found. Run create_messy_folder() first.")
        return
    
    print(f"\n📂 Scanning: {folder_path}")
    print("-" * 40)
    
    # Get all items in folder
    items = os.listdir(folder_path)
    
    for item in items:
        item_path = os.path.join(folder_path, item)
        
        # Skip directories (we only want files)
        if os.path.isdir(item_path):
            continue
        
        # Get file extension
        root, ext = os.path.splitext(item)
        ext = ext.lower()  # Normalize to lowercase
        
        # Remove the dot from extension (e.g., ".csv" → "csv")
        ext_name = ext[1:] if ext.startswith('.') else 'others'
        
        # Default folder name if extension unknown
        if ext_name == '':
            ext_name = 'others'
        
        # Create target subfolder
        target_folder = os.path.join(folder_path, ext_name)
        if not os.path.exists(target_folder):
            os.makedirs(target_folder)
            print(f"📁 Created folder: {ext_name}/")
        
        # Move the file
        target_path = os.path.join(target_folder, item)
        shutil.move(item_path, target_path)
        print(f"   Moved: {item} → {ext_name}/")
    
    print("\n✅ Folder organized!")

# Show the final structure
def show_structure():
    print("\n📂 Final folder structure:")
    for root, dirs, files in os.walk(folder_path):
        level = root.replace(folder_path, '').count(os.sep)
        indent = ' ' * 2 * level
        print(f"{indent}📁 {os.path.basename(root)}/")
        sub_indent = ' ' * 2 * (level + 1)
        for file in files:
            print(f"{sub_indent}📄 {file}")

# Run everything
if __name__ == "__main__":
    create_messy_folder()   # Comment this after first run
    organize_folder()
    show_structure()
```

---

## 📋 Functions Used in This Example

| Function | What it did |
|----------|--------------|
| `os.getcwd()` | Got current working directory |
| `os.path.join()` | Built safe file paths |
| `os.path.exists()` | Checked if folder/file existed |
| `os.makedirs()` | Created folders (including parent if needed) |
| `os.listdir()` | Scanned all items in a folder |
| `os.path.isdir()` | Checked if item is a directory (skip) |
| `os.path.splitext()` | Split file name and extension |
| `os.walk()` | Traversed entire folder structure |

---
