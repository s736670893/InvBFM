# InvBFM
We released three programs, InvBFM, fixRealData, and fixSimuData.    
Both fixRealData and fixSimuData are written in Shell for data preprocessing. 
InvBFM is written in Python which proposed in our paper.All three programs are packaged as executables, 
downloading from their source code and changed their permissions to executable for using as a tool.
<br/> <br/>
For example: chmod 777 InvBFM
## 1 Data preprocessing
### 1.1 fixRealData
The purpose of fixRealData is to is to detect inversions using existed tools.
<br/><br/>
Usage: <br/>
* ./fixRealData &lt; resultDirectory > &lt; realBamDirectory > &lt; realData.bam > &lt; referenceDirectory > &lt; referenceChrom.fa > &lt; referenceWholeGene.fa >
<br/><br/>
For example: ./fixRealData /home/realBamResult/ /home/bam/ NA19982.chrom11.ILLUMINA.bwa.ASW.low_coverage.20120522.bam /home/gao/ref/hs37d5/ 11.fa hs37d5.fa

### 1.2 fixSimuData
The purpose of fixRealData is to simulate inversion bam files.
<br/>
<br/>
Usage: 
<br/>
* ./fixSimuData &lt; simulatedTopDirectory > &lt; simulatedSecondaryDirectory > &lt; simulatedReference.fa > &lt; deviation > &lt; resultReference.fa > &lt; output > \"--Inv &lt; inversionNumber >--start: &lt; firstBreakpointLeftPosition >-end:&lt; firstBreakpointRightPosition > --size &lt; inversionLength >\" &lt; ISPE > &lt; ISSD > &lt; coverage > &lt; readLength >
<br/>
<br/>
For example: ./fixSimuData /home/simulateData3k/ INV3011_0.005/  hs37d5.fa 0.005 Seq.test.fa INV3011_0.005 "--Inv 61-start:45000-end:48010 --size 3011" 360 30 25X 128     

## 2 Inversion calls
Using "./InvBFM" to get usage of InvBFM.
<br/><br/>

Usage: <br/><br/>
* ./InvBFM -rt &lt; resSampleDirectory > &lt; pindelResultFile > &lt; pindelPointsFile > &lt; dellyResultFile > &lt; dellyPointsFile > &lt; lumpyexpressResultFile > &lt; lumpyexpressPointsFile > &lt; lumpyResultFile > &lt; lumpyPointsFile >
<br/><br/>
* ./InvBFM -rp &lt; pindelPointsFile > &lt; dellyPointsFile > &lt; lumpyPointsFile > &lt; lumpyexpressPointsFile > &lt; outputFile > &lt; mean_ISPE > &lt; ISSD >
<br/><br/>
* ./InvBFM -rm &lt; realDirectory > &lt; realFeatureFiles > &lt; outputPointsFile > &lt; outputFeaturesFile >
<br/><br/>
* ./InvBFM -fm &lt; minedPointsFile > &lt; outputFile > &lt; bamFile > &lt; "chromNumber" > &lt; mean_ISPE > &lt; ISSD >
<br/><br/>
* ./InvBFM -sn &lt; simulatedInversionPointsFile > &lt; simulatedNoInversionPointsFile >
<br/><br/>
* ./InvBFM -sm &lt; simulatedDirectory > &lt; simulatedFeatureFiles > &lt; outputFile >
<br/><br/>
* ./InvBFM -ci &lt; dataDirectory > &lt; trainDataFile > &lt; testDataFile > &lt; testPointsFile > &lt; outputFile >
<br/>
