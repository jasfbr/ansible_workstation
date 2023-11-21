# Descrição

Instala o Apache JMeter

Para restaurar o backup adicionar a opção restaurar_backup no playbook:

Exemplo:
```yaml
  - role: app-apache_jmeter-instalar
    restaurar_backup: true
```

# Dependências

## Coleções

## Funções

|Role|Task|
| :---: | :---: |
|commom|create_launcher|
| 

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
      jmeter:
        uri: 'https://dlcdn.apache.org/jmeter/binaries'
        file: 'apache-jmeter-5.6.2.tgz'
        install_dir: 'apache-jmeter-5.6.2'
        download_path: '{{downloads_path}}/apache'
```