# Tech - Sistema de Notícias com Autenticação OAuth 2.0

Uma aplicação web desenvolvida em Django que funciona como um portal de notícias de tecnologia. O grande diferencial deste projeto é o sistema de autenticação, que utiliza o protocolo OAuth 2.0 para permitir que os usuários façam login de forma segura utilizando suas contas do GitHub.

---

## 🚀 Tecnologias Utilizadas

*   **Python 3.x**
*   **Django 5.x** (Framework web principal)
*   **django-allauth** (Biblioteca para integração com OAuth 2.0)
*   **HTML5 / CSS3** (Camada de visualização)

---

## 🛠️ Como Executar o Projeto Localmente

Siga os passos abaixo para configurar o ambiente e rodar a aplicação na sua máquina:

### 1. Clonar o Repositório

```bash
git clone [https://github.com/jooli86/django-auth-oauth.git](https://github.com/jooli86/django-auth-oauth.git)
cd django-auth-oauth

2. Configurar o Ambiente Virtual (Venv)

# No Windows:
python -m venv venv
venv\Scripts\activate

# No Linux/Mac:
python3 -m venv venv
source venv/bin/activate

3. Instalar as Dependências

pip install -r requirements.txt

4. Rodar as Migrações do Banco de Dados

python manage.py migrate

5. Iniciar o Servidor de Desenvolvimento

python manage.py runserver

Agora, abra o seu navegador e acesse: http://127.0.0.1:8000/