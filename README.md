# 만든 chart를 압죽해서 docs/ 폴더 안에 저장
helm package charts/helm01_member -d docs/

# index.yaml 파일을 docs/ 폴더에 생성하기
helm repo index docs/ --url https://<github 아이디>.github.io/<github 저장소 이름>/
helm repo index docs/ --url https://pretty2753.github.io/MyHelmChart/

# 우리가 만든 helm chart 저장소를 사용해보기 

```bash
helm repo add my-repo https://pretty2753.github.io/MyHelmChart/

helm install member-release my-repo/member-app -n helm01 --create-namespace

# helm01_member 의 Chart.yaml 파일을 수정
version: 0.1.1
appVersion: "1.0.1"

# 수정 후의 helm package, index 를 다시 실행하고 add, commit, push 하면 자동으로
# github pages가 동작한다

helm package charts/helm01_member -d docs/

helm repo index docs/ --url https://pretty2753.github.io/MyHelmChart/
git add ./docs
git commit -m "release: member-app chart v1.0.1 package"
git push origin master

```

### 새로운 chart를 만들고 배포하기
```bash
helm package charts/helm02_micro -d docs/

# index.yaml 파일을 docs/ 폴더에 생성하기
helm repo index docs/ --url https://<github 아이디>.github.io/<github 저장소 이름>/
index.yaml 파일을 업데이트하기
helm repo index docs/ --url https://pretty2753.github.io/MyHelmChart/
```