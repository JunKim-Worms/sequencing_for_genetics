## 2주차 숙제
본격적인 숙제에 앞서 각 프로그램에 대해 간략하게 설명 드리도록 하겠습니다.\
먼저 `assembly-stats`, `bioawk`, `seqtk`는 모두 FASTA와 FASTQ 등 다양한 포맷을 다룰 수 있도록 도와주는 아주 빠르고 꽤 직관적인 도구들입니다.\
`assembly-stats`는 [N50](https://en.wikipedia.org/wiki/N50,_L50,_and_related_statistics)을 비롯해서 몇 가지 수치값을 간단하게 뽑아주는 도구로, 압축이 풀린 FASTA 또는 FASTQ에만 적용이 가능합니다. 다른 두 도구는 `gzip`으로 압축된 파일도 인풋으로 받을 수 있습니다.\
`bioawk`는 `awk`와 굉장히 유사한 도구입니다. `awk`가 행렬을 다루듯, `bioawk`는 각 포맷에 존재하는 다양한 정보, 예컨대 리드 이름, 염기서열, 품질값 등을 `awk`의 **컬럼**처럼 다룰 수 있게 도와줍니다. `awk '{print $1}'`이 첫 번째 컬럼을 뽑아주는 기능을 한다면 `bioawk -c fastx '{print $name}'`은 리드 이름만 쭉 뽑아주는 기능을 하는 셈입니다. [공식 홈페이지](https://github.com/lh3/bioawk)와 [다른 사람이 적어둔 설명서](https://bioinformaticsworkbook.org/Appendix/Unix/bioawk-basics.html#gsc.tab=0)에 나와있는 예제를 쭉 따라해보시면 bioawk에 대해 더 잘 이해하실 수 있을 겁니다.\
`seqtk`는 포맷 변경, GC 조성 확인, 랜덤 추출, 특정 리드 추출 등을 도와주는 도구입니다. 마찬가지로 [공식 홈페이지](https://github.com/lh3/seqtk)에 나와있는 예제를 따라해보시면 좋을 것 같습니다. 이 세 개 프로그램은 프로그램 이름만 치면 자세한 설명을 추가로 확인할 수 있으니 읽어보셔도 좋겠습니다. 예컨대 `seqtk`만 치면 이 프로그램으로 다룰 수 있는 다양한 하위 명령어들의 리스트가 출력되고, `seqtk sample` 등 하위 명령어까지 함께 쳐보면 사용례가 나오니 참고하세요.\
`samtools`는 FASTA 뿐만 아니라 이후에 배울 SAM 포맷을 다루는 데 널리 쓰이는 아주 유용한 도구입니다. 시퀀싱이 끝난 뒤에는 보통 표준 유전체(reference genome)에 시퀀싱된 리드를 갖다 붙이고(mapping or aligning) 비교하는 과정을 많이 거치게 되는데, 매핑이 얼마나 잘 됐는지 확인하거나 매핑된 파일을 압축하고 정렬하는 데 쓰입니다. 마찬가지로 [공식 홈페이지](http://www.htslib.org/doc/samtools.html)에 방문해봅시다.\
`hisat2`는 시퀀싱된 리드를 매핑해주는 프로그램입니다. 매핑하는 프로그램은 정말 많은데, 요새 graph genome 개념이 나오면서 새로 등장한 가벼운 도구입니다. 자세한 건 역시나 [공식 홈페이지](http://daehwankimlab.github.io/hisat2/)를 참고해주세요. DNA 시퀀싱 데이터를 다룰 때는 `bwa`나 `bowtie` 등이 많이 쓰이고, RNA 시퀀싱 데이터를 다룰 때는 `STAR`나 `kallisto` 등이 많이 쓰입니다.\

#### 다음 질문에 답해봅시다.
1) cb4856.pacbio.subseq.fq.gz은 *C. elegans* CB4856 strain의 [PacBio 롱리드 시퀀싱 결과](https://www.ncbi.nlm.nih.gov/sra/SRX5399849)에서 일부만 뽑아낸 것이다. 이 플랫폼에서는 다양한 길이의 리드가 생산되기 때문에 길이에 대한 정보를 알아둘 필요가 있다. 해당 파일에 포함된 리드의 수는? 평균값은? N50은? 가장 긴 리드의 길이는?\
2) cb4856.pacbio.subseq.fq.gz 파일에 포함된 10 kb 이상되는 리드의 개수는? 평균값은? N50은?\
3) srr3440952.sub.1.fq.gz과 srr3440952.sub.2.fq.gz은 같은 *C. elegans* CB4856 strain의 [Illumina 숏리드 시퀀싱 결과](https://www.ncbi.nlm.nih.gov/sra/SRX1727266)에서 일부만 뽑아낸 것이다. 해당 파일에 포함된 리드의 수는? 평균값은? N50은? 가장 긴 리드의 길이는?\
4) 가끔은 본격적인 분석을 하기 전에 랜덤 추출한 일부 리드만을 이용해 테스트 실험을 해보기도 한다. srr3440952.sub.1.fq.gz과 srr3440952.sub.2.fq.gz에서 리드를 100개씩 짝지어 추출하는 방법은?\
5) wbcel235.mt.fa는 [*C. elegans* reference genome](https://www.ncbi.nlm.nih.gov/assembly/GCF_000002985.6/)에서 마이토콘드리아 지놈만 뽑아놓은 것이다. 크기는? 이 파일에 포함된 ATGC를 소문자로 바꾸는 방법은? 다시 대문자로 바꾸는 방법은? MtDNA:100-200 구간의 염기서열 정보를 알아보는 방법은?\
6) 다음 명령어를 차례로 입력하면 CB4856 리드가 표준 마이토콘드리아 지놈에 매핑되고 정렬된 파일이 만들어집니다.\
```sh
hisat2-build wbcel235.mt.fa mt
hisat2 -x mt -1 srr3440952.sub.1.fq.gz -2 srr3440952.sub.2.fq.gz | samtools sort -O SAM -o mt.sam
```
매핑된 리드 수는? 리드 비율은?
