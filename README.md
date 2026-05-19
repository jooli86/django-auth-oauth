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
```

2. Configurar o Ambiente Virtual (Venv)
```bash
# No Windows:
python -m venv venv
venv\Scripts\activate
```

# No Linux/Mac:
```bash
python3 -m venv venv
source venv/bin/activate
```

3. Instalar as Dependências
```bash
pip install -r requirements.txt
```

4. Rodar as Migrações do Banco de Dados
```bash
python manage.py migrate
```

5. Iniciar o Servidor de Desenvolvimento
```bash
python manage.py runserver
```

## 🛠️ Evolução Técnica do Projeto

Durante o desenvolvimento deste ecossistema, o projeto foi refatorado e expandido para suportar padrões robustos de arquitetura e segurança de mercado.

### 1. Refatoração de Arquivos Estáticos (Pathlib)
*   **Modernização do Código:** Substituição do módulo legado `os.path` pela API moderna `pathlib`, garantindo gerenciamento de caminhos de arquivos mais legível, limpo e resiliente entre diferentes sistemas operacionais.
*   **Isolamento de Camadas:** Organização rigorosa da pasta `static/` na raiz do projeto, separando os arquivos de identidade visual (`css/`, `assets/`) das camadas de renderização HTML (`templates/`).

### 2. Integração do Ecossistema `django-allauth`
*   **Acoplamento Extensível:** Instalação e registro da biblioteca `django-allauth[socialaccount]` no núcleo do Django, tratando-a como uma extensão modular da aplicação.
*   **Interceptação por Middleware:** Configuração do `AccountMiddleware` na esteira de requisições do servidor, garantindo que o fluxo de autenticação seja verificado antes de atingir as views de negócio.
*   **Roteamento Centralizado:** Injeção das rotas nativas da biblioteca sob o prefixo `/accounts/`, disponibilizando endpoints automáticos de autenticação sem necessidade de codificação manual de formulários.

### 3. Fiação de Segurança OAuth 2.0 (Padrão de Mercado)
*   **Segurança da Informação:** Rejeição explícita da prática insegura de expor credenciais privadas (`client_id` e `secret`) diretamente no arquivo de texto `settings.py`.
*   **Acordo de Confiança (GitHub Developers):** Registro da aplicação sob o nome de **Tech News**, mapeando a URL de redirecionamento de segurança (*Authorization Callback URL*) de forma cirúrgica para o endpoint do sistema.
*   **Persistência Segura:** Armazenamento das chaves criptográficas geradas diretamente no banco de dados local através do painel de **Administração do Django (Admin)**. O arquivo do banco (`db.sqlite3`) encontra-se devidamente protegido no `.gitignore`, eliminando riscos de vazamento de credenciais no controle de versão.

### 4. Proteção de Rotas com Decorators e Segurança no HTML5
* **Cadeado no Backend:** Injeção do decorator `@login_required` na view de membros (`views.py`), blindando a rota exclusiva contra acessos diretos via digitação manual de URL.
* **Injeção de Tags Dinâmicas:** Implementação do disjuntor `{% load static %}` no novo template `members.html` para garantir a correta renderização dos ativos visuais e folhas de estilo.
* **Melhoria de Navegabilidade (UX):** Envelopamento semântico do logotipo da área de membros utilizando a tag dinâmica `{% url 'index' %}`, permitindo o retorno fluido à home page ao clicar na imagem.

### 5. Otimização e Lapidação do Fluxo de Autenticação (UX)
* **Redirecionamento de Acesso:** Configuração da diretriz `LOGIN_REDIRECT_URL = 'members'`, eliminando o erro nativo de página não encontrada (404 Profile) pós-autenticação.
* **Autenticação Direta (Bypass de Confirmação):** Ativação da flag `SOCIALACCOUNT_LOGIN_ON_GET = True`, permitindo que o clique no ícone social dispare imediatamente o redirecionamento para o GitHub, eliminando telas intermediárias.
* **Mapeamento de Logout Expresso:** Inclusão das flags `ACCOUNT_LOGOUT_ON_GET = True` e `LOGOUT_REDIRECT_URL = '/'` para automatizar a destruição da sessão ativa via requisição GET, preparando o terreno para o encerramento de sessão direto pela interface.