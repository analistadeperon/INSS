# INSS
<td style="font-family:arial; font-size:11px; text-align:center" valign="top">
            <a href="LINKAQUI" target="_blank">
                <img src="IMAGEM DO SEU SITE" border="0" />
            </a>
        </td>
        <td style="font-family:arial; font-size:12px; padding-left:10px">
            <strong>Seu nome</strong><br />
            <strong>Fone:</strong> (XX) XXXX XXXX<br />
            <strong>Site:</strong> <a href="LINKAQUI" target="_blank">SITEAQUI</a><br />
            <strong>Twitter/Instagram:</strong>REDES SOCIAIS<br />
            <strong>SKYPE:</strong> SEU SKYPE
        </td> 
    </tr>
</table>
<hr />

urlpatterns = [
    # '/'
    path('', 
      IndexTemplateView.as_view(), 
      name="index" # <<< Adicionar
    ),

    # '/funcionario/cadastrar'
    path('funcionario/cadastrar', 
      FuncionarioCreateView.as_view(), 
      name="cadastra_funcionario" # <<< Adicionar
    ),

    # '/funcionarios'
    path('funcionarios/', 
      FuncionarioListView.as_view(), 
      name="lista_funcionarios" # <<< Adicionar
    ),

    # '/funcionario/{pk}'
    path('funcionario/<pk>', 
      FuncionarioUpdateView.as_view(), 
      name="atualiza_funcionario" # <<< Adicionar
    ),

    # '/funcionarios/excluir/{pk}'
    path('funcionario/excluir/<pk>', 
      FuncionarioDeleteView.as_view(), 
      name="deleta_funcionario" # <<< Adicionar
    ),
]
 <!-- Favicon -->
    <link rel="shortcut icon" href="{% static 'website/img/favicon.png' %}" type="image/png">

    <!-- Arquivos CSS -->
    <link rel="stylesheet" href="{% static 'website/css/bootstrap.min.css' %}">
    <link rel="stylesheet" href="{% static 'website/css/master.css' %}">

    <!-- Bloco de Estilos -->
    {% block styles %}{% endblock %}
  </head>

  <body>
    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <a class="navbar-brand" href="{% url 'website:index' %}">
          <img src="{% static 'website/img/favicon.png' %}" height='45px'>
        </a>
        <button class="navbar-toggler" type="button" 
            data-toggle="collapse" data-target="#conteudo-navbar" 
            aria-controls="conteudo-navbar" aria-expanded="false" 
            aria-label="Ativar navegação">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="conteudo-navbar">
            <ul class="navbar-nav mr-auto">
                <li class="nav-item active">
                    <a class="nav-link" href="{% url 'website:index' %}">
                      Página Inicial
                    </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="{% url 'website:lista_funcionario' %}">
                      Funcionários
                    </a>
                </li>
            </ul>           
        </div>
    </nav>
      
    <!-- Bloco de conteúdo -->
    {% block conteudo %}{% endblock %}

    <!-- Arquivos necessários para o Bootstrap -->
    <script src="{% static 'website/js/jquery.min.js' %}"></script>
    <script src="{% static 'website/js/bootstrap.min.js' %}"></script>

    <!-- Bloco de scripts -->
    {% block scripts %}{% endblock %}

    <!-- Scripts.js -->
    <script src="{% static 'website/js/scripts.js' %}"></script>
  </body>
  !-- Bloco de conteúdo da nossa página -->    
{% block conteudo %}
<div class="container">
  <div class="row">
    <div class="col-lg-6 col-md-6 col-sm-6 col-xs-12">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">Cadastrar Funcionário</h5>
          <p class="card-text">
            Cadastre aqui um novo <code>Funcionário</code>.
          </p>
          <a href="{% url 'website:cadastra_funcionario' %}"
             class="btn btn-primary">
            Novo Funcionário
          </a>
        </div>
      </div>
    </div>
    <div class="col-lg-6 col-md-6 col-sm-6 col-xs-12">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">Lista de Funcionários</h5>
          <p class="card-text">
            Veja aqui a lista de <code>Funcionários</code> cadastrados.
          </p>
          <a href="{% url 'website:lista_funcionarios' %}"
             class="btn btn-primary">
            Vá para Lista
          </a>
        </div>
      </div>
    </div>
  </div>
</div>
{% endblock %}
{% extends "website/_layouts/base.html" %}

{% load widget_tweaks %}

{% block title %}Cadastro de Funcionários{% endblock %}

{% block conteudo %}
<div class="container">
  <div class="row">
    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">Cadastro de Funcionário</h5>
          <p class="card-text">
            Complete o formulário abaixo para cadastrar
            um novo <code>Funcionário</code>.
          </p>
          <form method="post">
            <!-- Não se esqueça dessa tag -->
            {% csrf_token %}

            <!-- Nome -->
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <span class="input-group-text">Nome</span>
              </div>
              {% render_field form.nome class+="form-control" %}
            </div>

            <!-- Sobrenome -->
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <span class="input-group-text">Sobrenome</span>
              </div>
              {% render_field form.sobrenome class+="form-control" %}
            </div>

            <!-- CPF -->
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <span class="input-group-text">CPF</span>
              </div>
              {% render_field form.cpf class+="form-control" %}
            </div>

            <!-- Tempo de Serviço -->
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <span class="input-group-text">Tempo de Serviço</span>
              </div>
              {% render_field form.tempo_de_servico class+="form-control" %}
            </div>

            <!-- Remuneração -->
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <span class="input-group-text">Remuneração</span>
              </div>
              {% render_field form.remuneracao class+="form-control" %}
            </div>

            <button class="btn btn-primary">Enviar</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</div>
{% endblock %}
class InsereFuncionarioForm(forms.ModelForm):
  ...
  nome = forms.CharField(
    max_length=255,
    widget=forms.TextInput(
      attrs={
        'class': "form-control"
      }
    )
  )
  ...
  {% extends "website/_layouts/base.html" %}

{% block title %}Lista de Funcionários{% endblock %}

{% block conteudo %}
<div class="container">
  <div class="row">
    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">Lista de Funcionário</h5>

          {% if funcionarios|length > 0 %}
            <p class="card-text">
              Aqui está a lista de <code>Funcionários</code> cadastrados.
            </p>

            <table class="table">
              <thead class="thead-dark">
              <tr>
                <th>ID</th>
                <th>Nome</th>
                <th>Sobrenome</th>
                <th>Tempo de Serviço</th>
                <th>Remuneração</th>
                <th>Ações</th>
              </tr>
              </thead>

              <tbody>
              {% for funcionario in funcionarios %}
                <tr>
                  <td>{{ funcionario.id }}</td>
                  <td>{{ funcionario.nome }}</td>
                  <td>{{ funcionario.sobrenome }}</td>
                  <td>{{ funcionario.tempo_de_servico }}</td>
                  <td>{{ funcionario.remuneracao }}</td>
                  <td>
                    <a href="{% url 'website:atualiza_funcionario' pk=funcionario.id %}"
                       class="btn btn-info">
                      Atualizar
                    </a>
                    <a href="{% url 'website:deleta_funcionario' pk=funcionario.id %}"
                      class="btn btn-outline-danger">
                        Excluir
                    </a>
                  </td>
                </tr>
              {% endfor %}
              </tbody>
            </table>
        {% else %}
          <div class="text-center mt-5 mb-5 jumbotron">
            <h5>Nenhum <code>Funcionário</code> cadastrado ainda.</h5>
          </div>
        {% endif %}
          <hr />
          <div class="text-right">
            <a href="{% url 'website:cadastra_funcionario' %}" class="btn btn-primary">
              Cadastrar Funcionário
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
{% endblock %}
{% extends "website/_layouts/base.html" %}

{% load widget_tweaks %}

{% block title %}Atualização de Dados do Funcionários{% endblock %}

{% block conteudo %}
<div class="container">
  <div class="row">
    <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">Atualização de Dados do Funcionário</h5>          
          <form method="post">
            <!-- Não se esqueça dessa tag -->
            {% csrf_token %}

            <!-- Nome -->
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <span class="input-group-text">Nome</span>
              </div>
              {% render_field form.nome class+="form-control" %}
            </div>

            <!-- Sobrenome -->
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <span class="input-group-text">Sobrenome</span>
              </div>
              {% render_field form.sobrenome class+="form-control" %}
            </div>

            <!-- CPF -->
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <span class="input-group-text">CPF</span>
              </div>
              {% render_field form.cpf class+="form-control" %}
            </div>

            <!-- Tempo de Serviço -->
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <span class="input-group-text">Tempo de Serviço</span>
              </div>
              {% render_field form.tempo_de_servico class+="form-control" %}
            </div>

            <!-- Remuneração -->
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <span class="input-group-text">Remuneração</span>
              </div>
              {% render_field form.remuneracao class+="form-control" %}
            </div>

            <button class="btn btn-primary">Enviar</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</div>
{% endblock %}
<!-- Estendemos do template base -->
{% extends "website/_layouts/base.html" %}

<!-- Bloco que define o <title></title> da nossa página -->
{% block title %}Página Inicial{% endblock %}

<!-- Bloco de conteúdo da nossa página -->
{% block conteudo %}
  <div class="container mt-5">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">Exclusão de Funcionário</h5>

        <p class="card-text">
          Você tem certeza que quer excluir o funcionário 
          <b>{{ funcionario.nome }}</b>?
        </p>

        <form method="post">
          {% csrf_token %}

          <hr />
          <div class="text-right">
            <a href="{% url 'website:lista_funcionarios' %}" 
              class="btn btn-outline-danger">
                Cancelar
            </a>
            <button class="btn btn-danger">Excluir</button>
          </div>
        </form>
      </div>
    </div>
  </div>
{% endblock %}
website/
   ...
   templatetags/
      __init__.py
      tempo_atual.py
      primeira_letra.py
  ...
  <p>{{ valor|primeira_letra }}</p>
  @register.filter(is_safe=True)
@stringfilter
def lower(value):
    """Convert a string into all lowercase."""
    return value.lower()
    from django import template
from django.template.defaultfilters import stringfilter

register = template.Library()

@register.filter
@stringfilter
def primeira_letra(value):
    return list(value)[0]
    <table class="table">
  <thead class="thead-dark">
    <tr>    
      <th><!-- Retiramos o "ID" aqui --></th>
      <th>Nome</th>
      <th>Sobrenome</th>
      <th>Tempo de Serviço</th>
      <th>Remuneração</th>
      <th class="text-center">Ações</th>
    </tr>
  </thead>
  <tbody>
    {% for funcionario in funcionarios %}
      <tr>
        <!-- Aplicamos nosso filtro no atributo funcionario.nome -->
        <td>{{ funcionario.nome|primeira_letra }}</td>
        <td>{{ funcionario.nome }}</td>
        <td>{{ funcionario.sobrenome }}</td>
        <td>{{ funcionario.tempo_de_servico }}</td>
        <td>{{ funcionario.remuneracao }}</td>
        <td class="text-center">
          <a href="{% url 'website:atualiza_funcionario' pk=funcionario.id %}"
              class="btn btn-primary">
            Atualizar
          </a>
          <a href="{% url 'website:deleta_funcionario' pk=funcionario.id %}"
            class="btn btn-danger">
              Excluir
          </a>
        </td>
      </tr>
    {% endfor %}
  </tbody>
</table>
import datetime
from django import template

register = template.Library()

@register.simple_tag
def tempo_atual():
    return datetime.datetime.now().strftime('%H:%M:%S')
    <body>
  <!-- Navbar -->
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
      ...
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav mr-auto">
              <li class="nav-item active">
                  <a class="nav-link" 
                    href="{% url 'website:index' %}">
                      Página Inicial
                  </a>
              </li>
              <li class="nav-item">
                  <a class="nav-link" 
                    href="{% url 'website:lista_funcionarios' %}">
                      Funcionários
                  </a>
              </li>
          </ul>
          <!-- Adicione a lista abaixo -->
          <ul class="navbar-nav float-right">
              <li class="nav-item">
                  <!-- Aqui está nosso filtro -->
                  <a class="nav-link" href="#">
                    <b>Hora: </b>{% tempo_atual %}
                  </a>
              </li>
          </ul>
      </div>
  </nav>
  ...
  {{ valor|capfirst }}
  {{ data|date:'d/m/Y' }}
  {{ valor|default:'Nenhum valor' }}
  {{ valor|first }}
  {{ valor|floatformat:"2" }}
  {% if valor|length > 0 %}
