mm3d RedTieP

mm3d Tapioca All ".*NEF" 1500 @SFS

mm3d Schnaps

3.4.3.3 Strategy :
compute on a small set of image a value of intrinsic calibration
• compute on a small set of image a value of intrinsic calibration, this set of image should be favorable to calibration; ideally, it should fulfill the following requirements :
– all image converging to same part of the scene,to facilitate the computation of external orientation
– a scene with sufficient depth variation ,to have accurate focal length estimation;
– a image acquisition where there position of the same ground points are located at very different position in the different images where they are seen, this is to have accurate estimation of
distortion; this can be obtained by rotating the camera like acquisition of figure 3.2




mm3d tapioca MulScale ".*NEF" 500 2000
mm3d tapas RadialStd  "../calib_init/.*NEF"  Out=init

mm3d tapas AutoCal  ".*NEF" InCal=Ori-init Out=Auto-all

Initialise orientation
mm3d Martini ".*NEF" InOri=init
//Tapas RadialBasic ".*NEF" Out=Rel InOri=Martini

AperiCloud
SaisieMasqQT
HomolFilterMasq
We can now use the HomolFilterMasq command to select the tie points that are inside the 3d masq. We use the
OriMasq3D option to indicate the orientation (necessary to compute by ray intersection the 3d point associated
to each tie point). By default, it assume that the mask has been seized on a AperiCloud result, and the default
name of the 3d mask is here AperiCloud All2 polyg3d.xml .
We have the to rename the homologous folder because by default all the MicMac command search the tie
points in the folder Homol :
mv Homol HomolInit
mv HomolMasqFiltered/ Homol


run Tapas taking into account the set of tie points without the sea;




4.1.2.4 Optional, scene-based orientation
Alternatively, if we do not have any GCP and want to put the data in an orientation having some physical
meaning, we can use the SBGlobBascule command (see 3.10.1.1) :
SBGlobBascule "(Face1|Face2|Lnk12)-IMGP[0-9]{4}.JPG" All MesureBascFace1.xml
PostPlan=_MasqPlanFace1 DistFS=2.0 Rep=ij
Glob
There is a new option Rep=ij, the meaning of this option is :
• it is a string that describe a repair;
• it must contain 2 symbols, each symbols can be in {i,-i,j,-j,k,-k} and describe a vector;
• the global orientation with be such that in the final orientation the line defined by Line1-Line2 is aligned
on first vector, and the normal to the plane is aligned on second vector;
• here in final orientation i will be the horizontal of the wall and j will be the normal to the wall, consequently
k = i ∧ j will be the vertical;




create durty mosaic to create a 2D or 3D masq



----
mm3d tapioca MulScale ".*NEF" 500 2000
mm3d tapas RadialStd  ".*NEF" Out=RS-All
mm3d C3DC Statue ".*NEF" RS-All
mm3d TiPunch C3DC_Statue.ply Filter=0 Depth=12
mm3d Tequila ".*NEF" RS-All  C3DC_Statue_mesh.ply


mm3d tapioca MulScale ".*NEF" 500 2000 @SFS
mm3d tapas RadialStd  ".*NEF" InCal=RS-All Out=RS-All-SFS
mm3d C3DC Statue ".*NEF" RS-All-SFS
mm3d TiPunch C3DC-SFS-Statue.ply  RS-All-SFS Filter=0 Depth=12
mm3d Tequila ".*NEF" RS-All-SFS  C3DC-SFS-Statue_poisson_depth12.ply


mm3d Malt GeomImage ".*.NEF"  RS-All NbProc=16 Master=DSC_9870.NEF   AffineLast=0





--- Par scene

#echo "scene1 -> done
mm3d Malt GeomImage "DSC_96((4[1-9])|([5-7][0-9])|(8[0-3])).NEF"  RS-All NbProc=16 Master=DSC_9671.NEF   AffineLast=0

#echo "scene2 -> done"
mm3d Malt GeomImage "DSC_9(6((8[4-9])|(9[0-9]))|7([0-1][0-9])).NEF"  RS-All NbProc=16 Master=DSC_9714.NEF  AffineLast=0

#echo "scene 3 -> done
mm3d Malt GeomImage "DSC_97((2[8-9])|(3[0-5])|(4[8-9])|(5[0-5])).NEF"  RS-All NbProc=16 Master=DSC_9748.NEF  AffineLast=0 (pas bonne master)
mm3d Malt GeomImage "DSC_97((2[8-9])|(3[0-5])|(4[8-9])|(5[0-5])).NEF"  RS-All NbProc=16 Master=DSC_9735.NEF  AffineLast=0 (pas bonne master)
mm3d Malt GeomImage "DSC_97(29|30|53|49|34|50).NEF"  RS-All NbProc=16 Master=DSC_9734.NEF  AffineLast=0

#echo "scene 4 -> done
mm3d Malt GeomImage "DSC_97((6[5-9])|([7-8][0-9])|(9[0-6])).NEF"  RS-All NbProc=16 Master=DSC_9772.NEF  AffineLast=0 (pas de bon resultat image profondeu tronqué on voit pas le petroglyphe)
mm3d Malt GeomImage "DSC_97((6[5-9])|([7-8][0-9])|(9[0-6])).NEF"  RS-All NbProc=16 Master=DSC_9775.NEF  AffineLast=0


#echo " scene 5 -> done
mm3d Malt GeomImage "DSC_98((3[7-9])|(4[0-9])|(5[0-8])|(1[3-9])).NEF"  RS-All NbProc=16 Master=DSC_9843.NEF  AffineLast=0

mm3d GrShade MM-Malt-Img-DSC_9671/Z_Num8_DeZoom1_STD-MALT.tif ModeOmbre=IgnE Mask=AutoMask_STD-MALT_Num_7.tif FZ=2 Out=Shade9671.tif
mm3d GrShade MM-Malt-Img-DSC_9748/Z_Num8_DeZoom1_STD-MALT.tif ModeOmbre=IgnE Mask=AutoMask_STD-MALT_Num_7.tif FZ=2 Out=Shade9748.tif
mm3d GrShade MM-Malt-Img-DSC_9714/Z_Num8_DeZoom1_STD-MALT.tif ModeOmbre=IgnE Mask=AutoMask_STD-MALT_Num_7.tif FZ=2 Out=Shade9714.tif
mm3d GrShade MM-Malt-Img-DSC_9749/Z_Num8_DeZoom1_STD-MALT.tif ModeOmbre=IgnE Mask=AutoMask_STD-MALT_Num_7.tif FZ=2 Out=Shade9749.tif
mm3d GrShade MM-Malt-Img-DSC_9772/Z_Num8_DeZoom1_STD-MALT.tif ModeOmbre=IgnE Mask=AutoMask_STD-MALT_Num_7.tif FZ=2 Out=Shade9772.tif
mm3d GrShade MM-Malt-Img-DSC_9843/Z_Num8_DeZoom1_STD-MALT.tif ModeOmbre=IgnE Mask=AutoMask_STD-MALT_Num_7.tif FZ=2 Out=Shade9843.tif

mm3d Nuage2Ply MM-Malt-Img-DSC_9671/NuageImProf_STD-MALT_Etape_8.xml Normale=5 Out=Fic0.ply
mm3d Nuage2Ply MM-Malt-Img-DSC_9714/NuageImProf_STD-MALT_Etape_8.xml Normale=5 Out=Fic1.ply
mm3d Nuage2Ply MM-Malt-Img-DSC_9748/NuageImProf_STD-MALT_Etape_8.xml Normale=5 Out=Fic2.ply
mm3d Nuage2Ply MM-Malt-Img-DSC_9772/NuageImProf_STD-MALT_Etape_8.xml Normale=5 Out=Fic3.ply

mm3d MergePly Fic.*.ply Out=mergedFic.ply Normale=1
