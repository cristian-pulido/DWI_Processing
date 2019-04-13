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
    ├── requirements.txt
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

## Ejecución tareas individuales 

 - Crear una carpeta que contenga:

	- La imagen de DWI en formato nifty 
	- Los archivos bvec y bval con el nombre "TENSOR" este se usa para identificarlos

 - Para ejecutar una tarea:
	
	-En una terminal con el ambiente virtual activo se usa el comando
	
	  python </path/of/task.py> </path/file.nii.gz> </path/folder/results>

	- Ej: python /home/user/Desktop/DWI_Processing/tareas/betDWI.py /home/user/Desktop/results/TENSOR.nii.gz /home/user/Desktop/results/

	- Tener en cuenta todos los resultados se guardan en la misma carpeta

	- Nota: Algunas tareas dependen de otras asi que si se ejecuta una tarea antes de haber ejecutado su dependencia generara un error

	- Dependencias de tareas
		
		-to_register_dwi_to_mni  depende de betDWI
		-to_estimate_dti depende de betDWI
		-to_estimate_dti_maps depende de to_estimate_dti
		-to_generate_bunddle depende de to_register_dwi_to_mni
		-to_generate_tractography depende de betDWI

## Orden recomendado de tareas 

	Entrada			Salida 			Tarea

	imagen original		1			eddy_correction
	1			2			nonLocalMean
	2			3			reslicing
	3			4 (b0,mask,dwi_masked)	betDWI
	4 (dwi_masked) 		5			to_register_dwi_to_mni
	4			6 (evecs,evlas)		to_estimate_dti
	4			7 maps(FA,AD,RD,MD)	to_estimate_dti_maps
	4			8 (feature,bundles)	to_generate_bunddle
	4			9 (tracto)		to_generate_tractography

	-Nota: ACtualmente las tareas al finalizar imprimen por pantalla el archivo que es necesario para la siguiente tarea con respecto a la tabla anterior.
	

   




