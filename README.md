# FastML2026 - KalEdge Tutorial


Before the session, there are only a couple of things to take care of. For access to the platform, please create an account at https://kaledge.kaleidoforge.com/ to get access.

## Tutorial Material

- **Tutorial Content**: `FastML2026_kalEdge.html`
- **Presentation**: `FastML2026-KalEdge-presentation.html`

## Artifacts

- **Models**: Pre-trained `.h5` model files ready for synthesis.
- **.xsa Files**: Pre-built bitstreams for the two HyperFPGA board types:
  - `4ge21`
  - `3be11`

## Dataset

The dataset used in this tutorial is publicly available on Zenodo. If you use it, please cite:
> Ballina Escobar, M. G., & Molina, R. S. (2026). Dataset of Scintillation Pulses for Pile-up Event Discrimination [Dataset]. Zenodo. https://doi.org/10.5281/zenodo.22110114


## HyperFPGA 
Access to the platform is available at https://hyperfpga.sti.ictp.it

## HyperFPGA files

### HyperFPGA Inference Notebook

This notebook demonstrates running a 1D-CNN model on a remote FPGA cluster for pulse classification.

- **Section 0: Setup**
  - Connects to the hyperfpga_cluster API, lists available FPGA board models, and reserves a target node (4ge21).
- **Section 1: FPGA Inference via AXI DMA**
  - **Load dataset**: Reads a CSV file with pulse data (61 features per sample), filters to classes 0 and 1, normalizes each pulse to the range [-1, 1], and converts to fixed-point integers (10 fractional bits) for hardware compatibility.
  - **Remote inference function (inference_axi_dma_remote)**: Runs on the remote FPGA node. It detects the AXI DMA hardware, writes all pulses to shared memory, then sends them to the FPGA one by one and collects two output values per pulse (the two class scores).
  - **Cluster launch and execution**: Creates a HyperFPGACluster, programs the FPGA with the "ml" firmware (XSA file), starts an ipyparallel engine via SSH, runs the inference function remotely, then cleanly shuts down and releases the FPGA node.
  - **Final predictions**: Converts the raw FPGA output to class predictions using argmax, then computes accuracy against the ground-truth labels. Result: 98.21% accuracy on 2400 pulses.
- **Section 2: Next steps**
  - Challenge for the user: extend the model to classify all 3 pulse classes (regular, pile-up, saturated), then re-synthesize and re-run on hardware.
