# Descrição

Instala a DownloadHelper bronwer extension. Extensão para download de vídeos.

# Dependências

## Coleções

## Funções

# Variáveis

## Vault

As variáveis que esta função precisa, devem ser colocadas no arquivo vault antes da executção do playbook:

```yaml
user:
  login: 
  group: 
downloads_path: 
```

## Inventário

As variáveis que esta função precisa, devem ser colocadas no inventário antes da executção do playbook:

```yaml
    app:
      downloadhelper:
        uri: 'https://github.com/mi-g/vdhcoapp/releases/download/v1.6.3'
        file: 'net.downloadhelper.coapp-1.6.3-1_amd64.deb'
        download_path: '{{downloads_path}}/downloadhelper'
```