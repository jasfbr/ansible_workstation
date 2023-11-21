# Descrição

Instala a extenção warsaw para acessar o Banco do Brasil.

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
      warsaw:
        uri: https://cloud.gastecnologia.com.br/bb/downloads/ws'
        file: 'warsaw_setup64.deb'
        download_path: '{{downloads_path}}/gastecnologia'
```