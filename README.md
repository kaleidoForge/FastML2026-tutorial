# FastML2026 - Tutorial

Before the session, there are only a couple of things to take care of. For access to the platform, please create an account at https://kaledge.kaleidoforge.com/ to get access.

## Tutorial Material

- **Tutorial Content**: `FastML2026_kalEdge.html`
- **Presentation**: `FastML2026-tutorial.html`

## Artifacts

- **IP Cores**
- **Models**
- **.xsa File**

## Dataset

The dataset used in this tutorial is publicly available on Zenodo. If you use it, please cite:
> Ballina Escobar, M. G., & Molina, R. S. (2026). Dataset of Scintillation Pulses for Pile-up Event Discrimination [Dataset]. Zenodo. https://doi.org/10.5281/zenodo.22110114


## HyperFPGA 
Access to the platform is available at https://hyperfpga.sti.ictp.it

## HyperFPGA files
- **Jupyter Notebook**


## Optional: On-Premises Installation

If you prefer to run the tutorial locally instead of using the Cloud Run platform, you can deploy it using Docker. You will need Docker and Docker Compose installed on your system.

Navigate to the `lic-trainig` folder and run:

```bash
cd lic-trainig
docker compose up -d
```

Once the container is running, open your web browser and navigate to `http://localhost:8503`.

**Default Credentials:**
* Administrator: `admin_training` / `training123`
* Standard User: `user` / `changeme`
