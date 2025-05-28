# Aseprite

## 빌드 방법
### 주의 사항
- 경로에 띄어쓰기나 한글이 포함되지 않아야 함

### 준비물
#### [Visual Studio](https://visualstudio.microsoft.com/)
빌드에 필요한 도구들을 설치하기 위해 필요

#### Ninja
```
choco install ninja
```

#### [Aseprite 소스 코드](https://github.com/aseprite/aseprite)
```
# ${aseprite_home}
git clone --recursive https://github.com/aseprite/aseprite.git
```

#### [Skia](https://github.com/aseprite/skia/releases)
- `Skia-Windows-Release-x64.zip`을 다운받아 사용함
- `${aseprite_home}/deps/skia-m124`에 압축을 풀어둠

### 설치 방법
- 최신 [공식 문서](https://github.com/aseprite/aseprite/blob/main/INSTALL.md)를 참고할 것
- 반드시 `cmd.exe`에서 실행해야 함

```
# ${aseprite_home}/aseprite
call "C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\Tools\VsDevCmd.bat" -arch=x64
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo -DLAF_BACKEND=skia -DSKIA_DIR=${aseprite_home}\deps\skia-m124 -DSKIA_LIBRARY_DIR=${aseprite_home}\deps\skia-m124\out\Release-x64 -DSKIA_LIBRARY=${aseprite_home}\deps\skia-m124\out\Release-x64\skia.lib -G Ninja ..
ninja aseprite
```

정상적으로 빌드되면 `${aseprite_home}/aseprite/build/bin/aseprite.exe`가 생성되어 있음
