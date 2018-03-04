# InvBFM
We released three programs, InvBFM, fixRealData, and fixSimuData.
Both fixRealData and fixSimuData are written in Shell for data preprocessing. 
InvBFM is written in Python which proposed in our paper.All three programs are packaged as executables, 
downloading from their source code and changed their permissions to executable for using as a tool.
<br /> <br />
For example: chmod 777 InvBFM
## 1 Data preprocessing
### 1.1 fixRealData
The purpose of fixRealData is to is to detect inversions using existed tools.
<br /><br />
Usage: <br />
./fixRealData <resultDirectory> <realBamDirectory> <realData.bam> <referenceDirectory> <referenceChrom.fa> <referenceWholeGene.fa>
<br /><br />
For example: ./fixRealData /home/realBamResult/ /home/bam/ NA19982.chrom11.ILLUMINA.bwa.ASW.low_coverage.20120522.bam /home/gao/ref/hs37d5/ 11.fa hs37d5.fa

### 1.2 fixSimuData
The purpose of fixRealData is to simulate inversion bam files.
<br /><br />
Usage: <br />
./fixSimuData <simulatedTopDirectory> <simulatedSecondaryDirectory> <simulatedReference.fa> <deviation> <resultReference.fa> <output> \"--Inv <firstStartPosition>--start:<>-end:<firstEndPosition> --size <inversionLength>\" <ISPE> <ISSD> <coverage> <readLength>
<br /><br />
For example: ./fixSimuData /home/simulateData3k/ INV3011_0.005/  hs37d5.fa 0.005 Seq.test.fa INV3011_0.005 "--Inv 61-start:45000-end:48010 --size 3011" 360 30 25X 128
## 2 Inversion calls
Using "./InvBFM" to get usage of InvBFM.
<br /><br />

Usage: <br /><br />
* ./InvBFM -rt resSampleDirectory  pindelResultFile  pindelPointsFile  dellyResultFile dellyPointsFile lumpyexpressResultFile lumpyexpressPointsFile lumpyResultFile lumpyPointsFile
<br /><br />
* ./InvBFM -rp pindelPointsFile dellyPointsFile lumpyPointsFile lumpyexpressPointsFile outputFile mean_ISPE ISSD
<br /><br />
* ./InvBFM -rm realDirectory realFeatureFiles outputPointsFile outputFeaturesFile
<br /><br />
* ./InvBFM -fm minedPointsFile outputFile bamFile "chromNumber" mean_ISPE ISSD
<br /><br />
* ./InvBFM -sn simulatedInversionPointsFile simulatedNoInversionPointsFile
<br /><br />
* ./InvBFM -sm simulatedDirectory simulatedFeatureFiles outputFile
<br /><br />
* ./InvBFM -ci dataDirectory trainDataFile testDataFile testPointsFile outputFile
<br />
