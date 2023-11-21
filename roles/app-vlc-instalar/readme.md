# Descrição

Instala e configura o VLC.

Para restaurar o backup adicionar a opção restaurar_backup no playbook:

Exemplo:
```yaml
  - role: app-vlc-instalar
    restaurar_backup: true
```

# Dependências

## Coleções

## Funções

|Role|Task|
| :---: | :---: |
|commom|restore_configuration_files|
| 

# Variáveis
As variáveis que esta função precisa, devem ser colocadas no arquivo vault antes da executção do playbook:

```yaml
backup_path: 
```

## Inventário
