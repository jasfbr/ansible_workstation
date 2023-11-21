# Descrição

Instala o jboss-cli do EAP 7.1

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
      jbosseap7:
        file: 'jboss-eap-7.1.0.zip'
        download_path: '{{downloads_path}}/redhat'
```