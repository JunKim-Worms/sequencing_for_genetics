## 1주차 숙제
#### 다음 명령어들 사용법 알아보기
```sh
[tab 버튼]
pwd
cd
./
../
ls
ls -l
rm
rm -r
cp
mv
ctrl + c
ctrl + z
ls *
ls *[0-9]
head
tail
head -2
tail -3
nano
less
vi
vi [어떻게 vi 빠져나오나]
wc
wc -l
sort
sort -r
sort -rV
| (pipe)
> (redirection)
cat
grep
grep --help
grep -c
grep ">"
grep $">tig00000[0-9][0-9]"
grep "^>"
grep -w "II"
awk
awk --help
awk '{print $2}'
sed
sed --help
sed -n '3,7p'
sed -n '3,7d'
sed 's/pilon//g'
echo
history
ctrl+r
seq
seq 0 100 10000
tar
tar -xzf
gzip
gzip -d
gunzip
gzip -cd
zcat
unzip
```

#### 다음 질문에 답해보기
1) lsp41_scaffolds.substr.fa 에 포함된 contig 개수는?(힌트: 모든 contig는 > 로 시작하는 문장 다음에 염기서열 정보가 따라옴)
2) cb4856.substr.fa 파일에 포함된 contig 개수는? 
3) cb4856.substr.fa 에 포함된 contig 이름은 "tig00015902|quiver|quiver|pilon|pilon" 등으로 되어있다. 여기서 |quiver|quiver|pilon|pilon 부분을 제거하고 싶다면 어떻게 해야 할까?
4) 2.0.bed 는 50 bp 이상의 structural variants에 관한 정보를 포함하는 tab으로 분리된 형식이다(tab-seperated values; tsv). 2번 염색체에는 몇 개의 variation이 존재하는가? (힌트: grep -P "\t" or grep -w or grep "\<\>")
5) 2번 염색체에 생긴 variation 중 insertion은 몇 개인가? (힌트: 7번째 컬럼 정보를 확인해보기)
6) 이 중 가장 큰 길이를 지닌 15개에 대한 정보만 포함하는 파일을 만들려면 어떻게 해야 하는가?
