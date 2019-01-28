# InvBFM
We released three programs, InvBFM, fixRealData, and fixSimuData.    
Both fixRealData and fixSimuData are written in Shell for data preprocessing. 
InvBFM is written in Python which proposed in our paper.All three programs are packaged as executables, 
downloading from their source code and changed their permissions to executable for using as a tool.
<br/> <br/>
For example: `chmod 777 InvBFM`
## 1 Data preprocessing
### 1.1 fixRealData
The purpose of fixRealData is to is to detect inversions based on existing tools.
<br/><br/>
Usage: <br/>
* ./fixRealData &lt; resultDirectory > &lt; realBamDirectory > &lt; realData.bam > &lt; referenceDirectory > &lt; referenceChrom.fa > &lt; referenceWholeGene.fa >
<br/><br/>
For example: `./fixRealData /home/realBamResult/ /home/bam/ NA19982.chrom11.bam /home/gao/ref/hs37d5/ 11.fa hs37d5.fa`

### 1.2 fixSimuData
The purpose of fixRealData is to simulate inversion bam files.
<br/>
<br/>
Usage: 
<br/>
* ./fixSimuData &lt; simulatedTopDirectory > &lt; simulatedSecondaryDirectory > &lt; simulatedReference.fa > &lt; deviation > &lt; resultReference.fa > &lt; output > \"--Inv &lt; inversionNumber >--start: &lt; firstBreakpointLeftPosition >-end:&lt; firstBreakpointRightPosition > --size &lt; inversionLength >\" &lt; ISPE > &lt; ISSD > &lt; coverage > &lt; readLength >
<br/><br/>
For example: `./fixSimuData /home/simulateData3k/ INV3011_0.005/  hs37d5.fa 0.005 Seq.test.fa INV3011_0.005 "--Inv 61-start:45000-end:48010 --size 3011" 360 30 25X 128`     

## 2 Inversion calls
### 2.1 InvBFM version 1.0
* `./InvBFM`  Getting usage of InvBFM.
<br/><br/>
		options:<br/>
		`./InvBFM -rt`	Usage for fixing Pindel/Delly/Lumpy/Lumpyexpress results for real bam.<br/>
		`./InvBFM -rp`	Usage for getting candidate inversions for a real bam.<br/>
		`./InvBFM -rm`	Usage for merging candidate inversions and its features from numeral real files.<br/>
		`./InvBFM -fm`	Usage for getting features selected by InvBFM.<br/>
		`./InvBFM -sn`	Usage for getting simulated no inversion points.<br/>
		`./InvBFM -sm`	Usage for merging inversion/NoInversion features for simulated data.<br/>
		`./InvBFM -ci`	Usage for calling true inversions by SVM.<br/>
### 2.2 Usage
* ./InvBFM -rt &lt; resultDirectory > &lt; pindelResultFile > &lt; pindelPointsFile > &lt; dellyResultFile > &lt; dellyPointsFile > &lt; lumpyexpressResultFile > &lt; lumpyexpressPointsFile > &lt; lumpyResultFile > &lt; lumpyPointsFile >
<br/><br/>
For example: `./InvBFM -rt /home/realBamResult/ pindelResult/NA19982_pindelResult_ pindelResult/NA19982_pindelPoints_ dellyResult/NA19982_dellyResult_ dellyResult/NA19982_dellyPoints_ lumpyexpressResult/NA19982_lumpyexpressResult_ lumpyexpressResult/NA19982_lumpyexpressPoints_ lumpyResult/NA19982_lumpyResult_ lumpyResult/NA19982_lumpyPoints_`
<br/><br/>
* ./InvBFM -rp &lt; pindelPointsFile > &lt; dellyPointsFile > &lt; lumpyPointsFile > &lt; lumpyexpressPointsFile > &lt; outputFile > &lt; mean_ISPE > &lt; ISSD >
<br/><br/>
For example: `./InvBFM -rp NA19982_pindelPoints_INV NA19982_dellyPoints_INV NA19982_lumpyPoints_INV NA19982_lumpyexpressPoints_INV NA19982_cadidatePoints_INV 320 37.5`
<br/><br/>
* ./InvBFM -rm &lt; resultDirectory > &lt; realFeatureFiles > &lt; outputPointsFile > &lt; outputFeaturesFile >
<br/><br/>
For example: `./InvBFM -rm /home/realBamResult/ realFeatureFilesList candidatePoints candidateFeatures`
<br/><br/>
* ./InvBFM -fm &lt; minedPointsFile > &lt; outputFile > &lt; bamFile > &lt; "chromNumber" > &lt; mean_ISPE > &lt; ISSD >
<br/><br/>
For example: `./InvBFM -fm points_INV features_INV sample.bam "11" 320 37.5`
<br/><br/>
* ./InvBFM -sn &lt; simulatedInversionPointsFile > &lt; simulatedNoInversionPointsFile >
<br/><br/>
For example: `./InvBFM -sn simulatedPoints_INV simulatedPoints_NoINV`
<br/><br/>
* ./InvBFM -sm &lt; simulatedDirectory > &lt; simulatedFeatureFiles > &lt; outputFile >
<br/><br/>
For example: `./InvBFM -sm /home/simulatedResult/ simulateFeatureFilesList simulatedFeatures`
<br/><br/>
* ./InvBFM -ci &lt; dataDirectory > &lt; trainDataFile > &lt; testDataFile > &lt; testPointsFile > &lt; outputFile >
<br/><br/>
For example: `./InvBFM -ci /home/result/ realFeatures simulatedFeatures candidatePoints finalInversions`
<br/><br/>
