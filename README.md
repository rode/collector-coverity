# collector-coverity

## Executing a scan
1. Install the coverity scan tool and add it to your path (OSX)
```
wget https://scan.coverity.com/download/java/macOSX
tar -xzf cov-analysis-macosx-2019.03.tar.gz 
export PATH=$PATH:$(pwd)/cov-analysis-macosx-2019.03/bin
```
2. cd into your build directory

3. Execute the scan
```
COVERITY_UNSUPPORTED=1 cov-build --dir cov-int mvn compile
```
4. Compress
```
tar czvf myproject.tgz cov-int
```
5. Upload (This can also be done through the UI)
```
curl --form token=NQ5bZMAopYVjo57tahh0rg \
  --form email=pafek47097@girtipo.com \
  --form file=@tarball/file/location \
  --form version="Version" \
  --form description="Description" \
  https://scan.coverity.com/builds?project=app
  
```