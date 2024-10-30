# myfsl docker project
## docker-build
```
docker build -t myfsl:<version> .
```
## docker-run
```
docker run -v <host absoulte input path>:/input -v <host absoulte output path>:/output dwnusa/myfsl:v1.0 run_first_all -i /input/cmc0001.nii -o /output/cmc0001 -s L_Accu,L_Caud,L_Puta,R_Accu,R_Caud,R_Puta
```


# tutorial
> https://open.win.ox.ac.uk/pages/fslcourse/website/online_materials.html

# tutorial 2
> https://fsl.fmrib.ox.ac.uk/fsl/docs/#/
