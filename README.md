# App e-mails modelo

Esse modelo serve para criarmos nossa app de e-mails seguindo um padrão.

Na hora de criar sua app basta digitar o seguinte comando:

```shell
python manage.py startapp --template https://github.com/TimeNovaData/app_emails_modelo/raw/master/emails.zip emails
```

Depois disso é só adiciona-la no seu settings.py e rodar os seguintes comandos:

```shell
python manage.py makemigrations
python manage.py migrate
```

Após isso adicione uma variável no seu .env chamada ENVIAR_EMAIL, dessa forma

```.env
ENVIAR_EMAIL=True
```

# Dependências

Eis aqui a lista de dependências da nossa app:

```txt
django-crum
django-quill-editor
```

Você pode instalá-los com o seguinte comando:

```shell
pip install django-crum
pip install django-quill-editor
pip freeze > requirements-dev.txt
```

# Exemplo de uso:

No admin, crie o seu template de e-mail, depois disso, escreva uma função para enviar o mesmo, dessa forma:

```python
def exemplo_email(self):
    from emails.models import MensagemEmail, TemplateEmail

    try:
        template_email = TemplateEmail.objects.get(codigo='the_code_of_email')
        mensagem_email = MensagemEmail.objects.create(template_email=template_email)
        mensagem_email.enviar()
    except:
        print('Provavelmente não existe um template de e-mail com esse código')
```

Depois de criar a função basta chamá-la, seja por meio de signals, condições, enfim, fica a seu critério!

# Deseja fazer melhorias?

Siga o passo a passo :)

1- Baixe o código

2- Faça as modificações que você deseja dentro da pasta app_modelo

3- Apague o arquivo .zip e depois crie um novo atualizado

4- Faça um pull request como de costume e pronto!

Obrigado por contribuir! o/
