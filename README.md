# aseprite-builder
Build Aseprite using Github action

# What should you do?
- fork this repo
- choose the platform you want to build
  ```yaml
  # file: .github/workflows/build_and_release.yaml
  # ...
  # lots of codes
  # ...
  build-aseprite:
    name: Build Aseprite
    needs: create-release
    permissions:
      contents: write
    runs-on: ${{ matrix.os }}
    strategy:
        matrix:
          os: [ windows-latest, ubuntu-latest, macOS-latest ] # <------- remove platform(s) you don't want
  ```
- **enable workflow `Build and release Aseprite` in `Actions -- Workflows`**
- **update `BuildLog.md` and push** (This step triggers the building process. You definitely want to do this!)
- now you should see the building process via `Actions` and you can find the product in `Release`

accroding to [Eula](https://github.com/aseprite/aseprite/blob/main/EULA.txt) :

> (b) Distribution.
> 
> You may not distribute copies of the SOFTWARE PRODUCT to third parties. Evaluation versions available for download from the Licensor's websites may be freely distributed.

we need to remove the product in `Releases` .

# FAQ

## libcrypto-1_1-x64.dll Not Found
Download [OpenSSL 1.1.1 binary for windows](https://kb.firedaemon.com/support/solutions/articles/4000121705-openssl-3-1-3-0-and-1-1-1-binary-distributions-for-microsoft-windows), and extract ```openssl-1.1\x64\bin\libcrypto-1_1-x64.dll``` to the PATH or aseprite home directory. 
