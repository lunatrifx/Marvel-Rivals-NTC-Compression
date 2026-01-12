# Marvel Rivals NTC Compression
One of Marvel Rivals' biggest problems that continues to grow as the game starts to pass one year of age is its game size. In August 2025, it was only 70 GB. Now it is 110 GB as of January 2026. Sure, content was added in heros, costumes, and new game modes but texture sizes tell a different story. That's where NVIDIA's newest SDK, Neural Texture Compression, comes into play. 

  Neural Texture Compression treats PBR (Physically Based Rendering) material bundles (Albedo, Normal, and Roughness maps) as a single neural unit rather than separate pixel blocks. This allows us to achieve 10x to 16x compression with minimal quality loss. 

  NTC leverages RTX graphics cards' tensor cores (surprise, AI much?) to inference, compress, and decompress bundles of textures all at once and extremely quickly into a single `.ntc` container. This algorithim in my instance is using inference-on-load. 

## Technical Brief

  Any NVIDIA graphics card that is supported by the latest drivers and has a good amount of tensor cores will work with this project. This was built on the RTX 5070 (Blackwell) generation, which comes with a lot of optimization features for neural networks, and includes the AI Management Processor which is critical for the usage of NTC as it works alongside the game as it runs, explained by [TechPowerUp's](https://www.techpowerup.com/review/nvidia-geforce-rtx-50-technical-deep-dive/3.html) analysis of the Blackwell architecture.

  Speaking of TechPowerUp, further explanation of AMP and how it can keep games flowing as smoothly as possible with external AI processes running:
  > The integration of AI models into gaming presents new challenges in maintaining a smooth and responsive experience. Scheduling becomes critical as both game rendering and AI tasks, like large language models (LLMs) for digital avatars, compete for resources. Delays in AI responses, known as "time to first response," can break immersion, while interruptions in game frame pacing can cause stutter. To address this, the AI Management Processor (AMP) was introduced as a programmable solution. Positioned at the front of the GPU, AMP precisely manages task scheduling, ensuring that AI processes, such as dialogue generation, do not interfere with game rendering, optimizing both smoothness and responsiveness for a seamless user experience.

![NVIDIA's powerpoint slide explaining AMP.](https://www.techpowerup.com/review/nvidia-geforce-rtx-50-technical-deep-dive/images/architecture-13.jpg)

The pipeline for this project follows the **"Compress Offline, Transcode at Runtime"** algorithm to maximize the progress made on storage savings without complicating the shader logic, which has been an issue with games that run on Unreal Engine 5. **The CUDA 12.4+ Toolkit is used**. 

## Findings (Will be added in the morning)

## Credits and Acknowledgements (Bibliography)

Special thanks to:

- FModel
- LibNTC
- Slang
- TechPowerUp
- CMake
- Visual Studio 2022 
- NVIDIA Research team for the "Real-Time Neural Apperarance Models" foundation. 
