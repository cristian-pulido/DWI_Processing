# DWI_Processing
Task for DWI images

## Instalación

 - Clonar repositorio
 - Crear Ambiente Virtual con dependencias:
          
          pip install -r requirements.txt
          
## Dependencias

  - FSL version 5.0.11 recomendada
          
## Estructura Carpetas

    ./
    ├── README.md
    ├── Atlas
    │   ├── 1mm
    │   │   ├──AAN.nii
    │   │   ├──HarvardOxfordCort.nii
    │   │   ├──Hypothalamus.nii
    │   │   ├──ThalamicNucleiMorelAtlas.nii
    │   │       
    │   └── 2mm
    │   │   ├──AAN.nii
    │   │   ├──HarvardOxfordCort.nii
    │   │   ├──Hypothalamus.nii
    │   │   ├──ThalamicNucleiMorelAtlas.nii
    │   │       
    ├── Tareas
    │   ├── dependencias
    │   └── betDWI.py
    │   └── eddy_correction.py
    │   └── medianOtsu.py
    │   └── nonLocalMean.py
    │   └── reslicing.py
    │   └── to_estimate_dti.py
    │   └── to_estimate_dti_maps.py
    │   └── to_generate_bunddle.py
    │   └── to_generate_tractography.py
    │   └── to_register_dwi_to_mni.py
   




