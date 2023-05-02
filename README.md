# payload dumper
Script testado em Yandex Amber OTA (completo e incremental) no Linux (mas pode funcionar no Windows também)

## Requisitos do sistema

-Python3, pip
- google protobuf para python `pip install protobuf`

### Docker

Como alternativa, você pode usar o Docker:
```
docker run --rm -v "${PWD}":/data -it vm03/payload_dumper /data/payload.bin --out /data
```
ou imagem do Docker de construção automática
```
# construa a imagem do contêiner
$ docker build -t payload_dumper .

# montar PWD atual e passar payload.bin
$ docker run --rm -v "${PWD}":/data -it payload_dumper /data/payload.bin --out /data

```

## Guia

### Preparação
- Certifique-se de ter o Python 3.6 ou posterior instalado.
- Baixe payload_dumper.py, update_metadata_pb2.py e requirements.txt
- Extraia seu zip OTA e coloque payload.bin na mesma pasta desses arquivos.
- Abra o PowerShell, prompt de comando ou terminal, dependendo do seu sistema operacional.
- Digite o seguinte comando: python -m pip install -r requirements.txt

### OTA Completo
- Quando terminar, digite este comando: python payload_dumper.py payload.bin
- Isso começará a extrair as imagens dentro do arquivo payload.bin para a pasta de saída em que você está.
### OTA incremental

- Copie as imagens originais (de OTA completo ou despejadas de dispositivos) para a pasta antiga (com nome da parte + .img, ex: boot.img, system.img)
- execute python payload_dumper.py --diff payload.bin
- arquivo extraído para a pasta de saída em que você está.
