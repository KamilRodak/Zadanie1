# stworzenie buildera
### użyte komendy
```
docker buildx create --name nowybuilder --driver docker-container --use
docker buildx inspect --bootstrap
```

### wynik komend
```
D:\Pliki\Pliki Studia\Programowanie_aplikacji_w_chmurze_obliczeniowej\Zadanie 1>docker buildx create --name nowybuilder --driver docker-container --use
nowybuilder

D:\Pliki\Pliki Studia\Programowanie_aplikacji_w_chmurze_obliczeniowej\Zadanie 1>docker buildx inspect --bootstrap
[+] Building 10.3s (1/1) FINISHED
 => [internal] booting buildkit                                                                                                                  10.3s
 => => pulling image moby/buildkit:buildx-stable-1                                                                                                9.0s
 => => creating container buildx_buildkit_nowybuilder0                                                                                            1.3s
Name:          nowybuilder
Driver:        docker-container
Last Activity: 2026-05-08 18:21:01 +0000 UTC

Nodes:
Name:                  nowybuilder0
Endpoint:              desktop-linux
Status:                running
BuildKit daemon flags: --allow-insecure-entitlement=network.host
BuildKit version:      v0.29.0
Platforms:             linux/amd64, linux/amd64/v2, linux/amd64/v3, linux/amd64/v4, linux/arm64, linux/riscv64, linux/ppc64le, linux/s390x, linux/386, linux/arm/v7, linux/arm/v6
Labels:
 org.mobyproject.buildkit.worker.executor:         oci
 org.mobyproject.buildkit.worker.hostname:         d4fb523ea96b
 org.mobyproject.buildkit.worker.network:          host
 org.mobyproject.buildkit.worker.oci.process-mode: sandbox
 org.mobyproject.buildkit.worker.selinux.enabled:  false
 org.mobyproject.buildkit.worker.snapshotter:      overlayfs
GC Policy rule#0:
 All:            false
 Filters:        type==source.local,type==exec.cachemount,type==source.git.checkout
 Keep Duration:  48h0m0s
 Max Used Space: 488.3MiB
GC Policy rule#1:
 All:            false
 Keep Duration:  1440h0m0s
 Reserved Space: 9.313GiB
 Max Used Space: 93.13GiB
 Min Free Space: 188.1GiB
GC Policy rule#2:
 All:            false
 Reserved Space: 9.313GiB
 Max Used Space: 93.13GiB
 Min Free Space: 188.1GiB
GC Policy rule#3:
 All:            true
 Reserved Space: 9.313GiB
 Max Used Space: 93.13GiB
 Min Free Space: 188.1GiB

```

# budowanie i wypchnięcie obrazu
### użyta komenda
```
ocker buildx build --platform linux/amd64,linux/arm64 -t kamilrodak/zadanie1:latest --cache-to type=registry,ref=kamilrodak/zadanie1:buildcache,mode=max --cache-from type=registry,ref=kamilrodak/zadanie1:buildcache --push .
```

### wynik pierwszego wykonania komendy
```
D:\Pliki\Pliki Studia\Programowanie_aplikacji_w_chmurze_obliczeniowej\Zadanie 1>docker buildx build --platform linux/amd64,linux/arm64 -t kamilrodak/zadanie1:latest --cache-to type=registry,ref=kamilrodak/zadanie1:buildcache,mode=max --cache-from type=registry,ref=kamilrodak/zadanie1:buildcache --push .
[+] Building 66.3s (32/32) FINISHED                                                                                       docker-container:nowybuilder
 => [internal] load build definition from Dockerfile                                                                                              0.0s
 => => transferring dockerfile: 994B                                                                                                              0.0s
 => resolve image config for docker-image://docker.io/docker/dockerfile:1                                                                         0.9s
 => [auth] docker/dockerfile:pull token for registry-1.docker.io                                                                                  0.0s
 => CACHED docker-image://docker.io/docker/dockerfile:1@sha256:2780b5c3bab67f1f76c781860de469442999ed1a0d7992a5efdf2cffc0e3d769                   0.0s
 => => resolve docker.io/docker/dockerfile:1@sha256:2780b5c3bab67f1f76c781860de469442999ed1a0d7992a5efdf2cffc0e3d769                              0.0s
 => [linux/arm64 internal] load metadata for docker.io/library/python:3.11-alpine                                                                 1.0s
 => [linux/amd64 internal] load metadata for docker.io/library/python:3.11-alpine                                                                 0.5s
 => [auth] library/python:pull token for registry-1.docker.io                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                 0.0s
 => => transferring context: 671B                                                                                                                 0.0s
 => ERROR importing cache manifest from kamilrodak/zadanie1:buildcache                                                                            0.9s
 => [internal] load build context                                                                                                                 0.1s
 => => transferring context: 5.45kB                                                                                                               0.0s
 => [linux/amd64 builder 1/4] FROM docker.io/library/python:3.11-alpine@sha256:8b5bfdb1fd2d78aa94e21c4d61be52487693f54be7f1021647751ff365795703   2.5s
 => => resolve docker.io/library/python:3.11-alpine@sha256:8b5bfdb1fd2d78aa94e21c4d61be52487693f54be7f1021647751ff365795703                       0.0s
 => => sha256:fd8e41ac72776720a5ce79d8a0c66e75ae8d3d836cb15cc6ae0682b0b7999a11 248B / 248B                                                        0.3s
 => => sha256:ea923c2ed79ed2d7163aacc54686501cb3339215671be89b50b62814aeffb95c 16.02MB / 16.02MB                                                  1.2s
 => => sha256:5c671a5c7ab3e0fe7526f4ff0a233b54727a1f407035f414a73138d2b0886733 455.65kB / 455.65kB                                                0.4s
 => => sha256:6a0ac1617861a677b045b7ff88545213ec31c0ff08763195a70a4a5adda577bb 3.86MB / 3.86MB                                                    0.7s
 => => extracting sha256:6a0ac1617861a677b045b7ff88545213ec31c0ff08763195a70a4a5adda577bb                                                         0.2s
 => => extracting sha256:5c671a5c7ab3e0fe7526f4ff0a233b54727a1f407035f414a73138d2b0886733                                                         0.4s
 => => extracting sha256:ea923c2ed79ed2d7163aacc54686501cb3339215671be89b50b62814aeffb95c                                                         0.9s
 => => extracting sha256:fd8e41ac72776720a5ce79d8a0c66e75ae8d3d836cb15cc6ae0682b0b7999a11                                                         0.0s
 => [auth] kamilrodak/zadanie1:pull token for registry-1.docker.io                                                                                0.0s
 => [linux/arm64 builder 1/4] FROM docker.io/library/python:3.11-alpine@sha256:8b5bfdb1fd2d78aa94e21c4d61be52487693f54be7f1021647751ff365795703   3.1s
 => => resolve docker.io/library/python:3.11-alpine@sha256:8b5bfdb1fd2d78aa94e21c4d61be52487693f54be7f1021647751ff365795703                       0.1s
 => => sha256:1e6fb1ada2c00ccee137e79b13fe7c1cbcb8599d6c1b1b4267724a5c3649c961 247B / 247B                                                        0.3s
 => => sha256:3e77490d7efda81dfe52b629a83d8948b45ba6b3146de01c60d870803a5e4b04 457.91kB / 457.91kB                                                0.3s
 => => sha256:d17f077ada118cc762df373ff803592abf2dfa3ddafaa7381e364dd27a88fca7 4.20MB / 4.20MB                                                    0.7s
 => => sha256:2d27834a976a180a5a91fa422f1ad444d4e03e2441fe5b64d5bc64630703bf2c 16.19MB / 16.19MB                                                  1.2s
 => => extracting sha256:d17f077ada118cc762df373ff803592abf2dfa3ddafaa7381e364dd27a88fca7                                                         0.2s
 => => extracting sha256:3e77490d7efda81dfe52b629a83d8948b45ba6b3146de01c60d870803a5e4b04                                                         0.2s
 => => extracting sha256:2d27834a976a180a5a91fa422f1ad444d4e03e2441fe5b64d5bc64630703bf2c                                                         0.9s
 => => extracting sha256:1e6fb1ada2c00ccee137e79b13fe7c1cbcb8599d6c1b1b4267724a5c3649c961                                                         0.0s
 => [linux/amd64 builder 2/4] WORKDIR /build                                                                                                      0.4s
 => [linux/amd64 stage-1 2/6] WORKDIR /app                                                                                                        0.4s
 => [linux/amd64 builder 3/4] COPY requirements.txt .                                                                                             0.1s
 => [linux/amd64 builder 4/4] RUN --mount=type=ssh pip install --no-cache-dir --prefix=/install -r requirements.txt                               7.9s
 => [linux/arm64 builder 2/4] WORKDIR /build                                                                                                      0.1s
 => [linux/arm64 stage-1 2/6] WORKDIR /app                                                                                                        0.1s
 => [linux/arm64 builder 3/4] COPY requirements.txt .                                                                                             0.1s
 => [linux/arm64 builder 4/4] RUN --mount=type=ssh pip install --no-cache-dir --prefix=/install -r requirements.txt                              39.7s
 => [linux/amd64 stage-1 3/6] COPY --from=builder /install /usr/local                                                                             0.1s
 => [linux/amd64 stage-1 4/6] COPY --chown=uzytkownik:uzytkownik zadanie1.py .                                                                    0.1s
 => [linux/amd64 stage-1 5/6] COPY --chown=uzytkownik:uzytkownik templates/ ./templates/                                                          0.1s
 => [linux/amd64 stage-1 6/6] RUN apk add --no-cache curl &&     adduser -D uzytkownik &&     rm -rf /var/lib/apt/lists/*                         1.3s
 => [linux/arm64 stage-1 3/6] COPY --from=builder /install /usr/local                                                                             0.1s
 => [linux/arm64 stage-1 4/6] COPY --chown=uzytkownik:uzytkownik zadanie1.py .                                                                    0.1s
 => [linux/arm64 stage-1 5/6] COPY --chown=uzytkownik:uzytkownik templates/ ./templates/                                                          0.0s
 => [linux/arm64 stage-1 6/6] RUN apk add --no-cache curl &&     adduser -D uzytkownik &&     rm -rf /var/lib/apt/lists/*                         3.1s
 => exporting to image                                                                                                                           13.9s
 => => exporting layers                                                                                                                           0.7s
 => => exporting manifest sha256:8a520cc498ea50f415bf8b4554185597d30c3a8d3320cd6bc16d57c072ac362c                                                 0.0s
 => => exporting config sha256:adc783c9c386ce54ec33ded9f2c9fbfcae7e74e6de1993fe48a6ca58658a8a40                                                   0.0s
 => => exporting attestation manifest sha256:e4a208f7e669642d96f5cbc344e895290d0d4ded78611bcccd67b5736ef2a7d3                                     0.0s
 => => exporting manifest sha256:eb1cd2d83ab73205b143c15c4376851dfb33acf5221b7c0805f3bce86cb897ff                                                 0.0s
 => => exporting config sha256:1f3f5b31e71ca60d0d7738d0a4a23aab9eb370d2ae6cc8dd285f5c6934cee0b5                                                   0.0s
 => => exporting attestation manifest sha256:63d9814b4652c9717f1cc2ee95a359537f5178e5a2b7646b359fcf8be527f476                                     0.0s
 => => exporting manifest list sha256:153ac4378321715d938e0cd355c7b8fc66d359e0c1f6e4be75f26047b8715b63                                            0.0s
 => => pushing layers                                                                                                                             8.4s
 => => pushing manifest for docker.io/kamilrodak/zadanie1:latest@sha256:153ac4378321715d938e0cd355c7b8fc66d359e0c1f6e4be75f26047b8715b63          4.7s
 => exporting cache to registry                                                                                                                  15.7s
 => => preparing build cache for export                                                                                                           1.9s
 => => sending cache export                                                                                                                      13.8s
 => => writing layer sha256:143f345b8c54091a22e189cadf5ee83fe26c230112a8ce40e70404b8750e9e9d                                                      7.2s
 => => writing layer sha256:01a1f8b384381ce5fd156b694725fcfe058194dc5cd4be711d8e98983bfc63b6                                                      7.7s
 => => writing layer sha256:04973d04886119d227f13f90f3279e5b753eec49d05e8cd7eb12085d723a935c                                                      6.9s
 => => writing layer sha256:0fe242e0670c1491d7878c58c8afd7642f8618eec8e0542f08438dd4c1b78b8a                                                      7.7s
 => => writing layer sha256:1e6fb1ada2c00ccee137e79b13fe7c1cbcb8599d6c1b1b4267724a5c3649c961                                                      0.1s
 => => writing layer sha256:1f07ed368ddb60ac778984ed7bfa0ee59a04abb3b998cc1bcb0f2e15c7fc68f9                                                      0.1s
 => => writing layer sha256:2d27834a976a180a5a91fa422f1ad444d4e03e2441fe5b64d5bc64630703bf2c                                                      0.1s
 => => writing layer sha256:32d796bc26c0124e8d23bf199f0c9e8b7d64811685c0099fc1705288aa67dd7c                                                      1.0s
 => => writing layer sha256:36441192f9b968f3cb12dbb5618bdca959e45e7ef2aceba0486a57b786e72271                                                      0.1s
 => => writing layer sha256:3e77490d7efda81dfe52b629a83d8948b45ba6b3146de01c60d870803a5e4b04                                                      0.1s
 => => writing layer sha256:5c671a5c7ab3e0fe7526f4ff0a233b54727a1f407035f414a73138d2b0886733                                                      0.1s
 => => writing layer sha256:64e3baae63d9e151d6010bf23c845413506b6944232c31c8f418a806c7e0fdf3                                                      1.1s
 => => writing layer sha256:6a0ac1617861a677b045b7ff88545213ec31c0ff08763195a70a4a5adda577bb                                                      0.1s
 => => writing layer sha256:7b333eadb26fec9701cd615a62b65a0c5217886945a2df06e7b409d02572e3d1                                                      3.2s
 => => writing layer sha256:8565b687bf1a1da42dabef248800f7158359e3eaf6ca2fe9cd36852e6256af01                                                      0.1s
 => => writing layer sha256:8f5589ad8288aef37fc9e304190ecd1590f4cde3e7aef5790ec1b15e60b366e7                                                      0.1s
 => => writing layer sha256:9475bd837ca61ef9bc209150eef647bb3615c3a2d5b022a85bbcfd0c1a2de1ab                                                      0.1s
 => => writing layer sha256:cf4482684add075dae4ac6f0d4f1aa46d6c1cff1c802fdc07c4242032e07d857                                                      1.1s
 => => writing layer sha256:d17f077ada118cc762df373ff803592abf2dfa3ddafaa7381e364dd27a88fca7                                                      0.1s
 => => writing layer sha256:e5d290ef75eeac7e646e72559cec7c8e1596942b834260a1d0b9abf65e5f3e57                                                      1.0s
 => => writing layer sha256:ea923c2ed79ed2d7163aacc54686501cb3339215671be89b50b62814aeffb95c                                                      0.1s
 => => writing layer sha256:ee16cba7fd1afbd6cba578233501c9d2bf040f0b1e7a6af5f0a1a06902392511                                                      0.1s
 => => writing layer sha256:f5646c37891b2da68e0edb89ffc9240212738bf42c1337057651058f506b0855                                                      0.1s
 => => writing layer sha256:fd8e41ac72776720a5ce79d8a0c66e75ae8d3d836cb15cc6ae0682b0b7999a11                                                      0.1s
 => => writing config sha256:8b98ea24a3ecbb66ef30338283ea557150f898487266749d0d62c0c1d2369ad2                                                     1.0s
 => => writing cache image manifest sha256:a4dbc907685738ab1ccb68690c32ee8f8b8f28576eb7847fe57801d7b136b3aa                                       1.9s
 => [auth] kamilrodak/zadanie1:pull,push token for registry-1.docker.io                                                                           0.0s
------
 > importing cache manifest from kamilrodak/zadanie1:buildcache:
------

View build details: docker-desktop://dashboard/build/nowybuilder/nowybuilder0/rpidciprctwsc1g8h7qbpqyte
```

### wynik drugiego wykonania komendy
```
D:\Pliki\Pliki Studia\Programowanie_aplikacji_w_chmurze_obliczeniowej\Zadanie 1>docker buildx build --platform linux/amd64,linux/arm64 -t kamilrodak/zadanie1:latest --cache-to type=registry,ref=kamilrodak/zadanie1:buildcache,mode=max --cache-from type=registry,ref=kamilrodak/zadanie1:buildcache --push .
[+] Building 74.3s (31/31) FINISHED                                                                                       docker-container:nowybuilder
 => [internal] load build definition from Dockerfile                                                                                              0.0s
 => => transferring dockerfile: 994B                                                                                                              0.0s
 => resolve image config for docker-image://docker.io/docker/dockerfile:1                                                                         1.3s
 => [auth] docker/dockerfile:pull token for registry-1.docker.io                                                                                  0.0s
 => CACHED docker-image://docker.io/docker/dockerfile:1@sha256:2780b5c3bab67f1f76c781860de469442999ed1a0d7992a5efdf2cffc0e3d769                   0.0s
 => => resolve docker.io/docker/dockerfile:1@sha256:2780b5c3bab67f1f76c781860de469442999ed1a0d7992a5efdf2cffc0e3d769                              0.0s
 => [linux/arm64 internal] load metadata for docker.io/library/python:3.12-alpine                                                                 1.0s
 => [linux/amd64 internal] load metadata for docker.io/library/python:3.12-alpine                                                                 0.6s
 => [auth] library/python:pull token for registry-1.docker.io                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                 0.0s
 => => transferring context: 671B                                                                                                                 0.0s
 => importing cache manifest from kamilrodak/zadanie1:buildcache                                                                                  1.6s
 => => inferred cache manifest type: application/vnd.oci.image.manifest.v1+json                                                                   0.0s
 => [linux/amd64 builder 1/4] FROM docker.io/library/python:3.12-alpine@sha256:236173eb74001afe2f60862de935b74fcbd00adfca247b2c27051a70a6a39a2d   1.9s
 => => resolve docker.io/library/python:3.12-alpine@sha256:236173eb74001afe2f60862de935b74fcbd00adfca247b2c27051a70a6a39a2d                       0.0s
 => => sha256:3a4f2e6e1560fccb75f8aa9c6b7458b3179164f6378b125e533286c88351cd2a 250B / 250B                                                        0.3s
 => => sha256:fd21a26fb55d22baaa317c98a4296e6a284dd39cc0f9e68ef781bb74adfd6dc7 13.74MB / 13.74MB                                                  1.1s
 => => sha256:254ac41e2afd13e7a1276627191463329b96d835eab35e7804fdad56d7e363d5 455.66kB / 455.66kB                                                0.4s
 => => extracting sha256:254ac41e2afd13e7a1276627191463329b96d835eab35e7804fdad56d7e363d5                                                         0.3s
 => => extracting sha256:fd21a26fb55d22baaa317c98a4296e6a284dd39cc0f9e68ef781bb74adfd6dc7                                                         0.6s
 => => extracting sha256:3a4f2e6e1560fccb75f8aa9c6b7458b3179164f6378b125e533286c88351cd2a                                                         0.0s
 => [internal] load build context                                                                                                                 0.0s
 => => transferring context: 137B                                                                                                                 0.0s
 => [linux/arm64 builder 1/4] FROM docker.io/library/python:3.12-alpine@sha256:236173eb74001afe2f60862de935b74fcbd00adfca247b2c27051a70a6a39a2d   2.3s
 => => resolve docker.io/library/python:3.12-alpine@sha256:236173eb74001afe2f60862de935b74fcbd00adfca247b2c27051a70a6a39a2d                       0.0s
 => => sha256:05b6ee55fad38c6a3dc2ee84c7a44ff2b3429fc3eef0d4c2a2cfeb230b0acd73 250B / 250B                                                        0.4s
 => => sha256:74bec20749987ddac4cc74bd2f826b97908f1c8a71661be8e89e6e8468e634d9 13.89MB / 13.89MB                                                  1.2s
 => => sha256:3124cc6c064bced8b2c441577d9c793d290258b2eb87477d21572e5a938fb3cb 457.92kB / 457.92kB                                                0.3s
 => => extracting sha256:3124cc6c064bced8b2c441577d9c793d290258b2eb87477d21572e5a938fb3cb                                                         0.3s
 => => extracting sha256:74bec20749987ddac4cc74bd2f826b97908f1c8a71661be8e89e6e8468e634d9                                                         0.6s
 => => extracting sha256:05b6ee55fad38c6a3dc2ee84c7a44ff2b3429fc3eef0d4c2a2cfeb230b0acd73                                                         0.0s
 => [linux/amd64 stage-1 2/6] WORKDIR /app                                                                                                        0.1s
 => [linux/amd64 builder 2/4] WORKDIR /build                                                                                                      0.1s
 => [linux/amd64 builder 3/4] COPY requirements.txt .                                                                                             0.0s
 => [linux/amd64 builder 4/4] RUN --mount=type=ssh pip install --no-cache-dir --prefix=/install -r requirements.txt                               6.8s
 => [linux/arm64 builder 2/4] WORKDIR /build                                                                                                      0.0s
 => [linux/arm64 stage-1 2/6] WORKDIR /app                                                                                                        0.0s
 => [linux/arm64 builder 3/4] COPY requirements.txt .                                                                                             0.0s
 => [linux/arm64 builder 4/4] RUN --mount=type=ssh pip install --no-cache-dir --prefix=/install -r requirements.txt                              47.6s
 => [linux/amd64 stage-1 3/6] COPY --from=builder /install /usr/local                                                                             0.1s
 => [linux/amd64 stage-1 4/6] COPY --chown=uzytkownik:uzytkownik zadanie1.py .                                                                    0.1s
 => [linux/amd64 stage-1 5/6] COPY --chown=uzytkownik:uzytkownik templates/ ./templates/                                                          0.1s
 => [linux/amd64 stage-1 6/6] RUN apk add --no-cache curl &&     adduser -D uzytkownik &&     rm -rf /var/lib/apt/lists/*                         1.4s
 => [linux/arm64 stage-1 3/6] COPY --from=builder /install /usr/local                                                                             0.1s
 => [linux/arm64 stage-1 4/6] COPY --chown=uzytkownik:uzytkownik zadanie1.py .                                                                    0.1s
 => [linux/arm64 stage-1 5/6] COPY --chown=uzytkownik:uzytkownik templates/ ./templates/                                                          0.1s
 => [linux/arm64 stage-1 6/6] RUN apk add --no-cache curl &&     adduser -D uzytkownik &&     rm -rf /var/lib/apt/lists/*                         3.6s
 => exporting to image                                                                                                                           14.0s
 => => exporting layers                                                                                                                           0.7s
 => => exporting manifest sha256:19b14a098a0bb3d6d052aadcbef7cdc46d7f9168b637da35d5e759bb21df1e3a                                                 0.0s
 => => exporting config sha256:7b4823d5873a8dce261f68fdf10d50e829c062834e90127dfcc7e96a932c1a75                                                   0.0s
 => => exporting attestation manifest sha256:dffa9833eacde83c657e273e3e176b8ad95a15d10b70d1deb480b122e8e4ad37                                     0.0s
 => => exporting manifest sha256:40ae6abfd95602746d6adee0af96e60ced702d062d984a0f1900d9e72729bbe2                                                 0.0s
 => => exporting config sha256:e3518d72e5f88042e86714133ac81b786e693a0caed186cea1364e052383f033                                                   0.0s
 => => exporting attestation manifest sha256:7822e87b05fb673c512f6f0012c9592cd9ce1f2b51c29cf0862f8f9461d7df0c                                     0.0s
 => => exporting manifest list sha256:84e19bd00074bbfb590bd859f6e3afafd4827c8154e6b11fdde4590f8e3e2722                                            0.0s
 => => pushing layers                                                                                                                             8.5s
 => => pushing manifest for docker.io/kamilrodak/zadanie1:latest@sha256:84e19bd00074bbfb590bd859f6e3afafd4827c8154e6b11fdde4590f8e3e2722          4.5s
 => exporting cache to registry                                                                                                                  14.6s
 => => preparing build cache for export                                                                                                           4.1s
 => => sending cache export                                                                                                                      10.5s
 => => writing layer sha256:146d46f7a0fb8a405eabed3a28d5133cdcac63b9181b292d2a1461d46997145d                                                      4.1s
 => => writing layer sha256:05b6ee55fad38c6a3dc2ee84c7a44ff2b3429fc3eef0d4c2a2cfeb230b0acd73                                                      4.1s
 => => writing layer sha256:11974f4a4a84767b1c3116a361c504a0b9cf3c3719c84c0ac1c32f21c4478c29                                                      4.7s
 => => writing layer sha256:169682da3f7b92366be2faf3d3bcbbf2df4b66b9494666a6c43fc2a48cb904a1                                                      0.1s
 => => writing layer sha256:254ac41e2afd13e7a1276627191463329b96d835eab35e7804fdad56d7e363d5                                                      0.1s
 => => writing layer sha256:269918d51422ef3a5431945fb58a13c2ac650faacd472f9dccdc419460cb7378                                                      2.2s
 => => writing layer sha256:3124cc6c064bced8b2c441577d9c793d290258b2eb87477d21572e5a938fb3cb                                                      0.1s
 => => writing layer sha256:3a4f2e6e1560fccb75f8aa9c6b7458b3179164f6378b125e533286c88351cd2a                                                      0.1s
 => => writing layer sha256:3d56a47d3e82a930c4cf0fb44e740808f16e6284c87dc8600996e15e4751158a                                                      0.8s
 => => writing layer sha256:40bd9c45882c7aaad4c38f997db3cf79b4e026ea75a9c73d39e7c8a3caaa0689                                                      0.1s
 => => writing layer sha256:69e733150c310805940f6887f1f562000ed3283c41e9070865f29bff810cb51d                                                      0.0s
 => => writing layer sha256:6a0ac1617861a677b045b7ff88545213ec31c0ff08763195a70a4a5adda577bb                                                      0.1s
 => => writing layer sha256:74bec20749987ddac4cc74bd2f826b97908f1c8a71661be8e89e6e8468e634d9                                                      0.1s
 => => writing layer sha256:78821c2cdac36ca01464ce37fcc5588db63840633d2ebb0cde0f6ea247bc541a                                                      0.1s
 => => writing layer sha256:85b28dbf59cbe2499b06954741b1f88271b055f9cadddce6ad55ae53ce13178e                                                      0.1s
 => => writing layer sha256:ce0f308a1f8a53487b8b6cee0ab1898b44a9d2a640ece84b05614565f7a2ed01                                                      0.1s
 => => writing layer sha256:d17f077ada118cc762df373ff803592abf2dfa3ddafaa7381e364dd27a88fca7                                                      0.1s
 => => writing layer sha256:d496981af3dcb452d8396ca756df86068d05cc767717e6a72e1d7e048b610815                                                      0.1s
 => => writing layer sha256:d6539c3d2bd1ece18f689541f3f503b902950429b8c3622946c761a491cdb7aa                                                      0.1s
 => => writing layer sha256:e2667a7d104ce29cd3d20fca4f19a28847aad3077a3ab5e97f5424bbbe30e93f                                                      1.9s
 => => writing layer sha256:fd21a26fb55d22baaa317c98a4296e6a284dd39cc0f9e68ef781bb74adfd6dc7                                                      0.1s
 => => writing config sha256:28e27e782f554ab217abc967be59501741e087f932151d7d5a2539d86ba3cef9                                                     1.0s
 => => writing cache image manifest sha256:f7ba4f3b692478683e030bd80074cbd5b51d17a1d3243d77e653043edcf974e0                                       1.9s
 => [auth] kamilrodak/zadanie1:pull,push token for registry-1.docker.io                                                                           0.0s

View build details: docker-desktop://dashboard/build/nowybuilder/nowybuilder0/vzyzc15asdz1jf6dd5fm3b2o9

```

# sprawdzenie architektur w rejestrze
### użyta komenda
```
docker buildx imagetools inspect kamilrodak/zadanie1:latest
```

### wynik komendy
```
D:\Pliki\Pliki Studia\Programowanie_aplikacji_w_chmurze_obliczeniowej\Zadanie 1>docker buildx imagetools inspect kamilrodak/zadanie1:latest
Name:      docker.io/kamilrodak/zadanie1:latest
MediaType: application/vnd.oci.image.index.v1+json
Digest:    sha256:153ac4378321715d938e0cd355c7b8fc66d359e0c1f6e4be75f26047b8715b63

Manifests:
  Name:        docker.io/kamilrodak/zadanie1:latest@sha256:8a520cc498ea50f415bf8b4554185597d30c3a8d3320cd6bc16d57c072ac362c
  MediaType:   application/vnd.oci.image.manifest.v1+json
  Platform:    linux/amd64

  Name:        docker.io/kamilrodak/zadanie1:latest@sha256:eb1cd2d83ab73205b143c15c4376851dfb33acf5221b7c0805f3bce86cb897ff
  MediaType:   application/vnd.oci.image.manifest.v1+json
  Platform:    linux/arm64

  Name:        docker.io/kamilrodak/zadanie1:latest@sha256:e4a208f7e669642d96f5cbc344e895290d0d4ded78611bcccd67b5736ef2a7d3
  MediaType:   application/vnd.oci.image.manifest.v1+json
  Platform:    unknown/unknown
  Annotations:
    vnd.docker.reference.digest: sha256:8a520cc498ea50f415bf8b4554185597d30c3a8d3320cd6bc16d57c072ac362c
    vnd.docker.reference.type:   attestation-manifest

  Name:        docker.io/kamilrodak/zadanie1:latest@sha256:63d9814b4652c9717f1cc2ee95a359537f5178e5a2b7646b359fcf8be527f476
  MediaType:   application/vnd.oci.image.manifest.v1+json
  Platform:    unknown/unknown
  Annotations:
    vnd.docker.reference.digest: sha256:eb1cd2d83ab73205b143c15c4376851dfb33acf5221b7c0805f3bce86cb897ff
    vnd.docker.reference.type:   attestation-manifest
```

# skanowanie obrazu przy użyciu trivy
### użyta komenda
```
trivy image --severity HIGH,CRITICAL kamilrodak/zadanie1:latest
```

### ostateczny wynik skanu
```
D:\Pliki\Pliki Studia\Programowanie_aplikacji_w_chmurze_obliczeniowej\Zadanie 1>trivy image --severity HIGH,CRITICAL kamilrodak/zadanie1:latest
2026-05-08T20:47:58+02:00       INFO    [vuln] Vulnerability scanning is enabled
2026-05-08T20:47:58+02:00       INFO    [secret] Secret scanning is enabled
2026-05-08T20:47:58+02:00       INFO    [secret] If your scanning is slow, please try '--scanners vuln' to disable secret scanning
2026-05-08T20:47:58+02:00       INFO    [secret] Please see https://trivy.dev/docs/v0.70/guide/scanner/secret#recommendation for faster secret detection
2026-05-08T20:48:00+02:00       INFO    [python] Licenses acquired from one or more METADATA files may be subject to additional terms. Use `--debug` flag to see all affected packages.
2026-05-08T20:48:01+02:00       INFO    Detected OS     family="alpine" version="3.23.4"
2026-05-08T20:48:01+02:00       INFO    [alpine] Detecting vulnerabilities...   os_version="3.23" repository="3.23" pkg_num=48
2026-05-08T20:48:01+02:00       INFO    Number of language-specific files       num=1
2026-05-08T20:48:01+02:00       INFO    [python-pkg] Detecting vulnerabilities...

Report Summary

┌──────────────────────────────────────────────────────────────────────────────────┬────────────┬─────────────────┬─────────┐
│                                      Target                                      │    Type    │ Vulnerabilities │ Secrets │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ kamilrodak/zadanie1:latest (alpine 3.23.4)                                       │   alpine   │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/blinker-1.9.0.dist-info/METADATA          │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/certifi-2026.4.22.dist-info/METADATA      │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/charset_normalizer-3.4.7.dist-info/METAD- │ python-pkg │        0        │    -    │
│ ATA                                                                              │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/click-8.3.3.dist-info/METADATA            │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/flask-3.1.3.dist-info/METADATA            │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/idna-3.13.dist-info/METADATA              │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/itsdangerous-2.2.0.dist-info/METADATA     │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/jaraco_context-6.1.2.dist-info/METADATA   │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/jinja2-3.1.6.dist-info/METADATA           │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/markupsafe-3.0.3.dist-info/METADATA       │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/packaging-26.2.dist-info/METADATA         │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/pip-25.0.1.dist-info/METADATA             │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/requests-2.33.1.dist-info/METADATA        │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/urllib3-2.7.0.dist-info/METADATA          │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/werkzeug-3.1.8.dist-info/METADATA         │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.12/site-packages/wheel-0.47.0.dist-info/METADATA           │ python-pkg │        0        │    -    │
└──────────────────────────────────────────────────────────────────────────────────┴────────────┴─────────────────┴─────────┘
Legend:
- '-': Not scanned
- '0': Clean (no security findings detected)
```

### poprzedni skan ze znalezionymi podatnościami
```
D:\Pliki\Pliki Studia\Programowanie_aplikacji_w_chmurze_obliczeniowej\Zadanie 1>trivy image --severity HIGH,CRITICAL kamilrodak/zadanie1:latest
2026-05-08T20:44:29+02:00       INFO    [vuln] Vulnerability scanning is enabled
2026-05-08T20:44:29+02:00       INFO    [secret] Secret scanning is enabled
2026-05-08T20:44:29+02:00       INFO    [secret] If your scanning is slow, please try '--scanners vuln' to disable secret scanning
2026-05-08T20:44:29+02:00       INFO    [secret] Please see https://trivy.dev/docs/v0.70/guide/scanner/secret#recommendation for faster secret detection
2026-05-08T20:44:31+02:00       INFO    [python] Licenses acquired from one or more METADATA files may be subject to additional terms. Use `--debug` flag to see all affected packages.
2026-05-08T20:44:31+02:00       INFO    Detected OS     family="alpine" version="3.23.4"
2026-05-08T20:44:31+02:00       INFO    [alpine] Detecting vulnerabilities...   os_version="3.23" repository="3.23" pkg_num=48
2026-05-08T20:44:31+02:00       INFO    Number of language-specific files       num=1
2026-05-08T20:44:31+02:00       INFO    [python-pkg] Detecting vulnerabilities...
2026-05-08T20:44:31+02:00       INFO    Table result includes only package filenames. Use '--format json' option to get the full path to the package file.

Report Summary

┌──────────────────────────────────────────────────────────────────────────────────┬────────────┬─────────────────┬─────────┐
│                                      Target                                      │    Type    │ Vulnerabilities │ Secrets │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ kamilrodak/zadanie1:latest (alpine 3.23.4)                                       │   alpine   │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/backports.tarfile-1.2.0.dist-info/METADA- │ python-pkg │        0        │    -    │
│ TA                                                                               │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/blinker-1.9.0.dist-info/METADATA          │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/certifi-2026.4.22.dist-info/METADATA      │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/charset_normalizer-3.4.7.dist-info/METAD- │ python-pkg │        0        │    -    │
│ ATA                                                                              │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/click-8.3.3.dist-info/METADATA            │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/flask-3.1.3.dist-info/METADATA            │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/idna-3.13.dist-info/METADATA              │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/itsdangerous-2.2.0.dist-info/METADATA     │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/jaraco_context-6.1.2.dist-info/METADATA   │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/jinja2-3.1.6.dist-info/METADATA           │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/markupsafe-3.0.3.dist-info/METADATA       │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/packaging-26.2.dist-info/METADATA         │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/pip-24.0.dist-info/METADATA               │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/requests-2.33.1.dist-info/METADATA        │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools-79.0.1.dist-info/METADATA      │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/autocommand-2.2.2.dis- │ python-pkg │        0        │    -    │
│ t-info/METADATA                                                                  │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/backports.tarfile-1.2- │ python-pkg │        0        │    -    │
│ .0.dist-info/METADATA                                                            │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/importlib_metadata-8.- │ python-pkg │        0        │    -    │
│ 0.0.dist-info/METADATA                                                           │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/inflect-7.3.1.dist-in- │ python-pkg │        0        │    -    │
│ fo/METADATA                                                                      │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/jaraco.collections-5.- │ python-pkg │        0        │    -    │
│ 1.0.dist-info/METADATA                                                           │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/jaraco.context-5.3.0.- │ python-pkg │        1        │    -    │
│ dist-info/METADATA                                                               │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/jaraco.functools-4.0.- │ python-pkg │        0        │    -    │
│ 1.dist-info/METADATA                                                             │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/jaraco.text-3.12.1.di- │ python-pkg │        0        │    -    │
│ st-info/METADATA                                                                 │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/more_itertools-10.3.0- │ python-pkg │        0        │    -    │
│ .dist-info/METADATA                                                              │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/packaging-24.2.dist-i- │ python-pkg │        0        │    -    │
│ nfo/METADATA                                                                     │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/platformdirs-4.2.2.di- │ python-pkg │        0        │    -    │
│ st-info/METADATA                                                                 │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/tomli-2.0.1.dist-info- │ python-pkg │        0        │    -    │
│ /METADATA                                                                        │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/typeguard-4.3.0.dist-- │ python-pkg │        0        │    -    │
│ info/METADATA                                                                    │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/typing_extensions-4.1- │ python-pkg │        0        │    -    │
│ 2.2.dist-info/METADATA                                                           │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/wheel-0.45.1.dist-inf- │ python-pkg │        1        │    -    │
│ o/METADATA                                                                       │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/setuptools/_vendor/zipp-3.19.2.dist-info- │ python-pkg │        0        │    -    │
│ /METADATA                                                                        │            │                 │         │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/urllib3-2.7.0.dist-info/METADATA          │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/werkzeug-3.1.8.dist-info/METADATA         │ python-pkg │        0        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/wheel-0.45.1.dist-info/METADATA           │ python-pkg │        1        │    -    │
├──────────────────────────────────────────────────────────────────────────────────┼────────────┼─────────────────┼─────────┤
│ usr/local/lib/python3.11/site-packages/wheel-0.47.0.dist-info/METADATA           │ python-pkg │        0        │    -    │
└──────────────────────────────────────────────────────────────────────────────────┴────────────┴─────────────────┴─────────┘
Legend:
- '-': Not scanned
- '0': Clean (no security findings detected)


Python (python-pkg)
===================
Total: 3 (HIGH: 3, CRITICAL: 0)

┌───────────────────────────┬────────────────┬──────────┬────────┬───────────────────┬───────────────┬──────────────────────────────────────────────────────────────┐
│          Library          │ Vulnerability  │ Severity │ Status │ Installed Version │ Fixed Version │                            Title                             │
├───────────────────────────┼────────────────┼──────────┼────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
│ jaraco.context (METADATA) │ CVE-2026-23949 │ HIGH     │ fixed  │ 5.3.0             │ 6.1.0         │ jaraco.context: jaraco.context: Path traversal via malicious │
│                           │                │          │        │                   │               │ tar archives                                                 │
│                           │                │          │        │                   │               │ https://avd.aquasec.com/nvd/cve-2026-23949                   │
├───────────────────────────┼────────────────┤          │        ├───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
│ wheel (METADATA)          │ CVE-2026-24049 │          │        │ 0.45.1            │ 0.46.2        │ wheel: wheel: Privilege Escalation or Arbitrary Code         │
│                           │                │          │        │                   │               │ Execution via malicious wheel file...                        │
│                           │                │          │        │                   │               │ https://avd.aquasec.com/nvd/cve-2026-24049                   │
│                           │                │          │        │                   │               │                                                              │
│                           │                │          │        │                   │               │                                                              │
│                           │                │          │        │                   │               │                                                              │
│                           │                │          │        │                   │               │                                                              │
└───────────────────────────┴────────────────┴──────────┴────────┴───────────────────┴───────────────┴──────────────────────────────────────────────────────────────┘
```

podatności zastały usunięte poprzez 
- zmiane obrazu bazowego z python:3.11-alpine na python:3.12-alpine
- aktualizację bibliotek wheel i jaraco.context w pliku requirements.txt