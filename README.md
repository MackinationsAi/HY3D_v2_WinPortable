## [HY3D_v2] - Hungyaun3D v2 Windows Portable

A self-contained, portable package for running **Hunyuan3D v2** on Windows w/ a custom gradio build.

### Features
- Convert **2D images** into **3D models** (Base Mesh & Textured Mesh)
- Supports **Text-to-3D** generation (enabled by default)
- Optimized for **low-VRAM** GPUs w/ fallback modes
- **One click finalize build** – portable and easy to use

---

## 1. System Requirements
### Minimum Requirements
- **Windows 10 or 11**
- **NVIDIA GPU** w/ at least **6GB VRAM** (4GB may work but will be slow)
- **CUDA Toolkit 12.8** (For texture generation)
- **Visual Studio Build Tools 2022** (For compiling)

### Recommended Setup
- **8GB+ VRAM** for full **shape + texture generation**
- **24GB+ RAM** for smooth processing
- **Latest NVIDIA drivers (March 2024 or newer)**

---

## 2. Installation & Setup

### Step 1: Download & Extract
1. Download **HY3D_v2_WinPortable.7z** from [GitHub Releases](https://github.com/MackinationsAi/HY3D_v2_WinPortable/releases)
2. Extract the **.7z** file to a location of your choice.

### Step 2: Download the models & finalize install
1. Open the extracted folder.
2. **Run** `run_build.bat`

### Step 3: (Optional) Install Dependencies for Texture Generation
To enable **textured model generation**, install:
- **CUDA Toolkit 12.8** ([Download](https://developer.nvidia.com/cuda-downloads))
- **Visual Studio Build Tools 2022** ([Download](https://aka.ms/vs/17/release/vs_BuildTools.exe))
  - During setup, **select**: **"Desktop Development w/ C++"**

### Step 4: Running the App
#### For High-VRAM GPUs (24GB)
- **Run** `boot_HY3D_v2.bat`
- **Access the WebUI**: Open [http://127.0.0.1:7860](http://127.0.0.1:7860) or [http://localhost:7860](http://localhost:7860)) in your browser.

#### For Low-VRAM GPUs (4GB-6GB)
- **Run** `boot_low_vram_HY3D_v2.bat`
- **Access the WebUI**: Open [http://127.0.0.1:7860](http://127.0.0.1:7860) or [http://localhost:7860](http://localhost:7860)
---

## 3. Usage Instructions
### Generating 3D Models
1. **Upload an image** or **enter a text prompt** in the WebUI.
2. **Click** "Generate Base Mesh Only" to get a **white 3D mesh**.
3. **Click** "Generate Base & Textured Meshes" (if texture generation is enabled).
4. View/download the **output** in the interface.

### Output Files
- 3D models are saved in:  
  ```
  HY3D_v2/outputs/'%Y-%m-%d'/'%H-%M-%S'_steps-{num_steps}_cfg-{cfg_scale}_res-{octree_resolution}_seed-{seed}/*here
  ```

---

## 4. Understanding the Files
### Main Scripts
| File | Description |
|------|------------|
| `HY3D_v2/upgradio_app.py` | The **Gradio WebUI app** script |
| `boot_HY3D_v2.bat` | Starts the app for **high VRAM GPUs** |
| `boot_low_vram_HY3D_v2.bat` | Starts the app for **low VRAM GPUs** |
| `dnld_models.bat` | Downloads **all required models (~39GB)** |
| `oc_install.bat` | One-time setup for **texture generation** |
| `run_build.bat` | Runs both  `dnld_models.bat` & `oc_install.bat` to install in one |

---

## 5. Troubleshooting
### Common Errors & Fixes
| Error | Solution |
|-------|----------|
| `CUDA out of memory` | Use **boot_low_vram_HY3D_v2.bat**. |
| `Can't load TensorRT` | Ignore – The app will fallback to CUDA. |
| `Texture generation not working` | Ensure CUDA & VS Build Tools are installed, then re-run `oc_install.bat`. |
| `Models not found` | Run `dnld_models.bat` again. |

---

## 6. Additional Features & Customization
### Changing WebUI Theme
1. Open the app and go to **UI Settings**.
2. Select a new theme.
3. Restart the app.

### Proxy Setup (For Restricted Networks)
If you need a proxy, **add this** to your `.bat` scripts:
```bat
set HTTP_PROXY=http://your-proxy.com:[port]
set HTTPS_PROXY=http://your-proxy.com:[port]
```

---

## 7. Credits
* Modified & Re-packaged by **MackinationsAi** ([GitHub](https://github.com/MackinationsAi))
  
* Special thanks to the researchers, developers, and all contributors of
https://github.com/Tencent/Hunyuan3D-2[Hunyuan3D 2.0], & [YanWenKun](https://github.com/YanWenKun) for laying out a lot of the ground work w/ their winportable version. Kudos to [DeepBeepMeep](https://github.com/deepbeepmeep) for creating [mmgp](https://github.com/deepbeepmeep/mmgp) & [Hunyuan3D-2GP](https://github.com/deepbeepmeep/Hunyuan3D-2GP) for bringing Hunyuan3D 2.0 to less-capable GPUs.