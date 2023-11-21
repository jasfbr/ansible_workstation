# Descrição

Instala o jboss-cli do EAP 6.4

# Dependências

## Coleções

## Funções

# Variáveis

## Vault

As variáveis que esta função precisa, devem ser colocadas no arquivo vault antes da executção do playbook:

```yaml
user:
  login: 
downloads_path:
```

## Inventário

As variáveis que esta função precisa, devem ser colocadas no inventário antes da executção do playbook:

```yaml
app:
  jbosseap6:
    jdk:
      file: 'jdk-7u80-linux-x64.tar.gz'
      download_path: '{{downloads_path}}/oracle'
    file: 'jboss-eap-6.4.0.zip'
    download_path: '{{downloads_path}}/redhat'
```