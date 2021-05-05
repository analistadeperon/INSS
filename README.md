# INSS
JS Starter
Formulario DE como Pagar seu funcionarios: {# base.html contém o template que usaremos como esqueleto #} {% extends "base.html" %} {% block conteudo %}
{{ section.Name }}
{% for funcionario in funcionarios %}
{{ funcionario.nome|upper }}
TEMPLATES = [ { 'BACKEND': 'django.template.backends.django.DjangoTemplates', 'DIRS': [], 'APP_DIRS': True, 'OPTIONS': {}, }, ] {% endfor %} {% endblock %} urlpatterns = [ # '/' path('', IndexTemplateView.as_view(), name="index" # <<< Adicionar ), # '/funcionario/cadastrar' path('funcionario/cadastrar', FuncionarioCreateView.as_view(), name="cadastra_funcionario" # <<< Adicionar ), # '/funcionarios' path('funcionarios/', FuncionarioListView.as_view(), name="lista_funcionarios" # <<< Adicionar ), # '/funcionario/{pk}' path('funcionario/', FuncionarioUpdateView.as_view(), name="atualiza_funcionario" # <<< Adicionar ), # '/funcionarios/excluir/{pk}' path('funcionario/excluir/', FuncionarioDeleteView.as_view(), name="deleta_funcionario" # <<< Adicionar ), ] {% block styles %}{% endblock %}
 
Página Inicial
Funcionários
{% block conteudo %}{% endblock %} {% block scripts %}{% endblock %} !-- Bloco de conteúdo da nossa página --> {% block conteudo %}
Cadastrar Funcionário
Cadastre aqui um novo Funcionário.

Novo Funcionário
Lista de Funcionários
Veja aqui a lista de Funcionários cadastrados.

Vá para Lista
{% endblock %} {% extends "website/_layouts/base.html" %} {% load widget_tweaks %} {% block title %}Cadastro de Funcionários{% endblock %} {% block conteudo %}
Cadastro de Funcionário
Complete o formulário abaixo para cadastrar um novo Funcionário.

{% csrf_token %}
Nome
{% render_field form.nome class+="form-control" %}
Sobrenome
{% render_field form.sobrenome class+="form-control" %}
CPF
{% render_field form.cpf class+="form-control" %}
Tempo de Serviço
{% render_field form.tempo_de_servico class+="form-control" %}
Remuneração
{% render_field form.remuneracao class+="form-control" %}
Enviar
{% endblock %} class InsereFuncionarioForm(forms.ModelForm): ... nome = forms.CharField( max_length=255, widget=forms.TextInput( attrs={ 'class': "form-control" } ) ) ... {% extends "website/_layouts/base.html" %} {% block title %}Lista de Funcionários{% endblock %} {% block conteudo %}
Lista de Funcionário
{% if funcionarios|length > 0 %}
Aqui está a lista de Funcionários cadastrados.

{% for funcionario in funcionarios %} {% endfor %}
ID	Nome	Sobrenome	Tempo de Serviço	Remuneração	Ações
{{ funcionario.id }}	{{ funcionario.nome }}	{{ funcionario.sobrenome }}	{{ funcionario.tempo_de_servico }}	{{ funcionario.remuneracao }}	Atualizar Excluir{% else %}
Nenhum Funcionário cadastrado ainda.
{% endif %}
Cadastrar Funcionário
{% endblock %} {% extends "website/_layouts/base.html" %} {% load widget_tweaks %} {% block title %}Atualização de Dados do Funcionários{% endblock %} {% block conteudo %}
Atualização de Dados do Funcionário
{% csrf_token %}
Nome
{% render_field form.nome class+="form-control" %}
Sobrenome
{% render_field form.sobrenome class+="form-control" %}
CPF
{% render_field form.cpf class+="form-control" %}
Tempo de Serviço
{% render_field form.tempo_de_servico class+="form-control" %}
Remuneração
{% render_field form.remuneracao class+="form-control" %}
Enviar
{% endblock %} {% extends "website/_layouts/base.html" %} {% block title %}Página Inicial{% endblock %} {% block conteudo %}
Exclusão de Funcionário
Você tem certeza que quer excluir o funcionário {{ funcionario.nome }}?

{% csrf_token %}
Cancelar Excluir
{% endblock %} website/ ... templatetags/ __init__.py tempo_atual.py primeira_letra.py ...
{{ valor|primeira_letra }}

@register.filter(is_safe=True) @stringfilter def lower(value): """Convert a string into all lowercase.""" return value.lower() from django import template from django.template.defaultfilters import stringfilter register = template.Library() @register.filter @stringfilter def primeira_letra(value): return list(value)[0] {% for funcionario in funcionarios %} {% endfor %}
Nome	Sobrenome	Tempo de Serviço	Remuneração	Ações
{{ funcionario.nome|primeira_letra }}	{{ funcionario.nome }}	{{ funcionario.sobrenome }}	{{ funcionario.tempo_de_servico }}	{{ funcionario.remuneracao }}	Atualizar Excluirimport datetime from django import template register = template.Library() @register.simple_tag def tempo_atual(): return datetime.datetime.now().strftime('%H:%M:%S')
...
Página Inicial
Funcionários
Hora: {% tempo_atual %}
... clique aqui clique aqui
