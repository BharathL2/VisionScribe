# VisionScribe: An Open-Source Image and Video Labeler

[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)](#prerequisites)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.x-blue.svg)](https://opencv.org/)

An intuitive tool for labeling images and videos for computer vision tasks, supporting multiple annotation formats like **PASCAL VOC** and **YOLO**. This project is an enhanced version based on the original **OpenLabeling** tool.

<p align="center">
  <img src="Untitled%20video%20-%20Made%20with%20Clipchamp%20(3).gif" width="45%">
</p>



---

## ✨ Features

- **Multiple Annotation Formats:** Native support for **PASCAL VOC** (XML) and **YOLO** (txt) formats.
- **Video Object Tracking:** Integrated with OpenCV trackers (**CSRT, KCF, MOSSE**, etc.) to accelerate video annotation.
- **Deep Learning Assistance:** Optionally use pre-trained models to pre-fill bounding boxes and speed up labeling.
- **User-Friendly GUI:** Simple keyboard and mouse shortcuts for efficient labeling, editing, and navigation.
- **Autosave & Recovery:** Periodic saving of labels to prevent accidental data loss. *(Optional)*
- **Cross-Platform:** Works on Windows, macOS, and Linux.

---

## 📚 Table of Contents

- [Quick Start](#-quick-start)
- [Prerequisites](#-prerequisites)
- [How to Run](#-how-to-run)
- [Command-Line Arguments](#-command-line-arguments)
- [GUI Usage](#-gui-usage)
  - [Keyboard Shortcuts](#keyboard-shortcuts)
  - [Mouse Controls](#mouse-controls)
- [Project Structure](#-project-structure)
- [FAQ](#-faq)
- [Contributing](#-contributing)
- [Author](#-author)

---

## 🚀 Quick Start

Clone the repository (replace placeholders with your actual GitHub details):

```bash
git clone https://github.com/BharathL2/VisionScribe
cd VisionScribe
```

---

## 🧰 Prerequisites

You need **Python 3.8+** and several packages installed.

Update pip:

```bash
python -m pip install -U pip
```

Install required packages from `requirements.txt`:

```bash
python -m pip install -U -r requirements.txt
```

This will install (at minimum): `opencv-contrib-python`, `numpy`, `tqdm`, and `lxml`.

**Install PyTorch (Optional):** Required for some advanced tracking features like *DaSiamRPN*.
Visit the official [PyTorch website](https://pytorch.org/get-started/locally/) for installation instructions specific to your OS and CUDA setup.

---

## ▶️ How to Run

1. Navigate to the `main/` directory inside the project folder.
2. Place your images and videos into the `input/` folder.
3. Define your object classes in `class_list.txt` (one class per line).
4. Run the main script from your terminal:

```bash
python main.py
```

Your generated labels will be saved in the `output/` folder.

---

## ⚙️ Command-Line Arguments

You can customize the tool's behavior with the following arguments:

```bash
python main.py [-h] [-i <path>] [-o <path>] [-t <int>] [--tracker <type>] [-n <int>]
```

**Options**

- `-i, --input` — Path to your input folder. *(Default: `input/`)*  
- `-o, --output` — Path to your output folder. *(Default: `output/`)*  
- `-t, --thickness` — Bounding box line thickness. *(Default: `1`)*  
- `--tracker` — Tracker to use for video annotation (`CSRT`, `KCF`, `MOSSE`, etc.).  
- `-n` — Number of frames to track an object automatically.

**Example:**

```bash
python main.py --input ./data/videos --output ./labels --tracker CSRT -n 15 --thickness 2
```

---

## 🖱️ GUI Usage

### Keyboard Shortcuts

| Key | Description |
|-----|-------------|
| `d` | Next image |
| `a` | Previous image |
| `w` | Next class |
| `s` | Previous class |
| `e` | Show/hide bounding box edges |
| `p` | Predict next frames in video |
| `h` | Show help dialog |
| `q` | Quit the application |

### Mouse Controls

- **Draw Box:** Left-click for the top-left corner, then left-click again for the bottom-right corner.  
- **Quick Delete:** Right-click on a bounding box to delete it instantly.  
- **Select Box:** Double-click a bounding box to select it for editing.  
- **Zoom:** Use the middle mouse wheel to zoom in and out.

---

## 🗂 Project Structure

```
VisionScribe/
├─ main/
│  ├─ main.py
│  ├─ utils/...
│  └─ trackers/...
├─ input/                # Put your images/videos here
├─ output/               # Auto-saved labels (VOC/YOLO)
├─ class_list.txt        # One class per line
├─ requirements.txt
├─ README.md
└─ LICENSE
```

---

## ❓ FAQ

**Q: How do I add a new class?**  
Add a new line with the class name in `class_list.txt` and restart the app.

**Q: Can I label videos frame-by-frame?**  
Yes. You can step through frames and use the tracker (`--tracker`) to propagate boxes automatically for `-n` frames.

**Q: How do I export in YOLO vs VOC?**  
Set the desired format in the app/config (or via a CLI flag if provided). The tool writes compatible files per class and frame/image.

**Q: I get an error importing OpenCV trackers.**  
Ensure you installed **opencv-contrib-python** (not just `opencv-python`).

---

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repo
2. Create a feature branch: `git checkout -b feat/your-feature`
3. Commit your changes: `git commit -m "feat: add your feature"`
4. Push to the branch: `git push origin feat/your-feature`
5. Open a Pull Request

For major changes, open an issue first to discuss what you would like to change.


---

## 👤 Author

**Bharath L** — [https://github.com/BharathL2]  

> Feel free to contribute by forking this repository and submitting a pull request!
