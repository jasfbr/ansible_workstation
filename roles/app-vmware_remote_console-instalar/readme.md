# Descrição

Instala e o VMware REmote Console.

# Dependências

## Coleções

## Funções

# Variáveis

## Vault

## Inventário

As variáveis que esta função precisa, devem ser colocadas no inventário antes da executção do playbook:

```yaml
    app:
      vmrc:
        file: 'VMware-Remote-Console-12.0.1-18113358.x86_64.bundle'
        download_path: '{{downloads_path}}/vmware'
```