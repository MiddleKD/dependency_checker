# dependency_checker
test code의 실행에 있어 필수적인 패키지들을 확인하고, 필요없는 패키지를 제거합니다.

## USAGE
### :pencil2: `conda activate`또는 `source venv activate` 가상환경을 활성화한 후 사용해야 합니다.

**install init packages**
```bash
python3 dependency_check.py --install [True] --initpkg [list of packages] --target [venv path]
```
* `--install`: 패키지를 설치하는 모드로 진입합니다.
* `--initpkg`(optional): 추가로 설치해야 하는 패키지를 지정합니다. `dependency_check.py`파일 내의 init_packages가 있지만, 추가로 더 필요할 때 사용합니다.
* `--target`(optional): 패키지들을 저장하는 장소를 변경하는데 사용합니다.

**check dependency**
```bash
python3 dependency_check.py --check [True] --device [device] --target [venv path]
```
* `--check`: 패키지의 의존성을 판단하는 모드로 진입합니다. 설치된 패키지의 리스트를 받아온 후,
    * 패키지 삭제
    * 테스트코드 실행
    * 패키지 재설치
    과정을 거칩니다. 진행 중 오류 발생시, `dependency_check.py`파일의 삭제 예외 패키지 이름을 추가할 수 있습니다.
    테스트코드를 실행하는데 필요한 패키지와 불필요한 패키지는 `dependency_check.json`파일에 저장됩니다.
* `--device`(optional): 테스트코드에 `pytorch gpu`코드가 포함될 경우, device를 설정할 수 있습니다.
* `--target`(optional): 패키지들을 저장하는 장소를 변경하는데 사용합니다.

**remove unnecessary packages**
```bash
python3 dependency_check.py --remove [True] --target [venv path]
```
* `--remove`: 불필요한 패키지를 삭제하는 모드로 진입합니다. `dependency_check.json`의 `unnecessary_packages`를 삭제합니다.
* `--target`(optional): 패키지들을 저장하는 장소를 변경하는데 사용합니다.
