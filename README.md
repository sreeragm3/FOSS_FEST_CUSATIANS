# Dekko Rich Text Plugin

A Qt/QML plugin for the [Dekko email client](https://gitlab.com/dekkan/dekko) that adds **HTML/Markdown email composition** support.  
**Targets Issue [#164](https://gitlab.com/dekkan/dekko/-/issues/164)**.

---

## Features
- 🛠 **Rich Text Toolbar**: Bold, italic, lists, and HTML mode toggle  
- 📝 **Markdown Support**: Write in Markdown, preview as HTML  
- 🔒 **HTML Sanitization**: Strips unsafe tags before sending emails  
- 🧩 **Modular Design**: Works alongside Dekko's core without modifications  
- 🖥 **Qt6 Compatibility**: Built with modern CMake and QML modules  

---

## Installation

### 1. Clone as a Submodule
```bash
# From Dekko's root directory:
git submodule add https://github.com/sreeragm3/FOSS_FEST_CUSATIANS.git plugins/richtext
```

### 2. Update CMake Build
Add to Dekko's CMakeLists.txt:
```
# Inside Dekko's main CMakeLists.txt:
add_subdirectory(plugins/richtext)
```

### 3. Rebuild Dekko
```
mkdir build && cd build
cmake -DCMAKE_PREFIX_PATH=/path/to/qt6 ..  # Adjust Qt6 path as needed
make -j4
```

---

## Configuration
### 1. Replace Composer Window
Modify Dekko's composer launcher (e.g., dekko.qml):
```
// Before:
// var comp = d.getComponent("Dekko::Mail::Composer");

// After:
var comp = d.getComponent("Dekko::RichText::RichComposerWindow");
```

### 2. Enable Plugin in QML
Import the plugin in your QML files:
```
import Dekko.RichText 1.0
```

---

## Usage
### Toolbar Actions
| Button      | Action                                                    |
|-------------|-----------------------------------------------------------|
| B           | Wraps selected text in bold (Markdown) or <strong> (HTML) |
| I           | Wraps selected text in italic (Markdown) or <em> (HTML)   |
| • List      | Inserts a bulleted list                                   |
| HTML Toggle | Switches between HTML/Markdown and plaintext modes        |

---

## Development
### Dependencies
- Qt 6.2+ (Core, QML, Quick)
- marked.js (Bundled in src/lib/)

### Build Standalone
```
git clone https://gitlab.com/sreeragm3/FOSS_FEST_CUSATIANS.git
cd dekko-rich-text-plugin
mkdir build && cd build
cmake .. && make
```

###File Structure
```
src/
├── qml/              # QML components
├── lib/              # Third-party JS/CSS
└── backend/          # C++ logic (sanitization, mode switching)
```

---

## License
GNU GPLv3 (Compatible with Dekko's licensing)
See LICENSE for details.
