# Build notes - Medical Imaging & Digital Pathology

Repo2RLEnv pr_diff (v0.9.6), Harbor-format output. Domain: medical-imaging-pathology.

## Funnel

| Stage | Count |
|---|---|
| Domain candidates (deduped) | 647 |
| After active+star+noise filter | 273 |
| Final target list (cap 200) | 200 |
| Repos with >=1 task | 116 |
| Repos with 0 tasks | 84 |
| Total tasks (<=3/repo) | 245 |

## Generation

- Shared task bank: each repo generated once (pr_diff, limit=3,
  max_files_per_pr=15, min_loc_changed=2), 4-way concurrency,
  rate-limit-aware with .done checkpoint resume.
- Per-domain consolidation: rank by reward_calibration.loc_changed desc,
  keep at most 3 tasks per repo. Zero-yield repos are NOT fabricated.
- Overlap with the 3 published cancer editions is allowed (user decision);
  domains are independent selections, not a partition of one repo set.

## Zero-yield repos (informational, 84)

- amusi/CVPR2026-Papers-with-Code
- extreme-assistant/CVPR2024-Paper-Code-Interpretation
- qubvel-org/segmentation_models.pytorch
- Charmve/Surface-Defect-Detection
- linhandev/dataset
- Beckschen/TransUNet
- sherlockchou86/VideoPipe
- MrGiovanni/UNetPlusPlus
- extreme-assistant/ICCV2023-Paper-Code-Interpretation
- amusi/ECCV2026-Papers-with-Code
- JunMa11/SOTA-MedSeg
- InsightSoftwareConsortium/ITK
- MIC-DKFZ/medicaldetectiontoolkit
- JunMa11/MICCAI-OpenSourcePapers
- YichiZhang98/SAM4MIS
- qqlu/Entity
- neeru1207/AI_Sudoku
- xiaoyufenfei/Efficient-Segmentation-Networks
- souvikmajumder26/Multi-Agent-Medical-Assistant
- uni-medical/SAM-Med3D
- adalca/medical-datasets
- DCMTK/dcmtk
- nyukat/breast_cancer_classifier
- usuyama/pytorch-unet
- JCruan519/VM-UNet
- caiyuanhao1998/SAX-NeRF
- baidu-research/NCRF
- mikeroyal/ISP-Guide
- cgohlke/tifffile
- horosproject/horos
- tue-mps/eomt
- shenyunhang/APE
- hitachinsk/SAMed
- YubiaoYue/MedMamba
- JJGO/UniverSeg
- ge-xing/SegMamba
- maduc7/Histopathology-Datasets
- jeya-maria-jose/UNeXt-pytorch
- CUHK-AIM-Group/U-KAN
- mlavik1/UnityVolumeRendering
- rishikksh20/ResUnet
- mahmoodlab/CONCH
- Amshaker/unetr_plus_plus
- eidelen/DicomToMesh
- WZH0120/SAM2-UNet
- openmedlab/MedLSAM
- RobvanGastel/dinov3-finetune
- MedAIerHHL/CVPR-MIA
- FirasGit/medicaldiffusion
- cheng-01037/Self-supervised-Fewshot-Medical-Image-Segmentation
- pyushkevich/itksnap
- BAAI-DCAI/M3D
- Rubics-Xuan/TransBTS
- ethanhe42/u-net
- MrBlankness/LightM-UNet
- xinzhichao/Underwater_Datasets
- MrGiovanni/SuPreM
- vietanhdev/samexporter
- BhanuPrakashNani/Image_Processing
- BAAI-DCAI/SegVol
- HUANGLIZI/LViT
- jeya-maria-jose/KiU-Net-pytorch
- PathologyFoundation/plip
- MrGiovanni/SyntheticTumors
- slideflow/slideflow
- HMS-Core/hms-ml-demo
- wurenkai/UltraLight-VM-UNet
- yifangao112/Camyla
- SLDGroup/EMCAD
- yhygao/CBIM-Medical-Image-Segmentation
- icon-lab/SynDiff
- caiyuanhao1998/X-Gaussian
- Mycenae/PaperWeekly
- YtongXie/CoTr
- yifangao112/DinoUNet
- abachaa/Existing-Medical-QA-Datasets
- Beckschen/3D-TransUNet
- yhlleo/DeepSegmentor
- rordenlab/MRIcroGL
- camicroscope/caMicroscope
- junforge-dev/DicomVisionClient
- SuboptimalEng/volume-rendering
- webnamics/u-dicom-viewer
- wisdomikezogwo/quilt1m

## Caveats

- Static validation only; real grading needs an LLM judge key + Docker.
- inline_dockerfile mode skips image build (no Docker daemon needed to publish).
- Provider secrets in upstream diffs were redacted before public release.
