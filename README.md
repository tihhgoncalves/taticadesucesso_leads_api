# API de Leads da Tática de Sucesso

API oficial de documentação de Leads da Tática de Sucesso.
Esta é a primeira versão da API, ainda em versão beta, algumas mudanças e melhorias serão implementadas futuramente.

### Sumário

- [Apenas JSON](#apenas-json)
- [Requisições](#requisições)
    - [Consultar Listas](#consultar-listas) ```GET /lists```
    - [Cadastrar Lead](#cadastrar-lead) ```GET /lead```
- [Script de Formulários](#script-de-formulários)
    

### A URL base da API:
 
```endpoint``` http://leads.taticadesucesso.com.br

# Apenas JSON

A API só suporta JSON, nós não vamos dar suporte a outro formato. Mesmo que você não utilize o header ```Content-Type: application/json; charset=utf-8``` a resposta será em JSON e com charset utf-8.

# Requisições

---

### Consultar Listas
Faz consulta de todas as Listas de Leads disponíveis.

#### Requisição:

```GET /lead```

#### Parâmetros
 - (nenhum)

#### Resposta:

```json
{
    "code": "202",
    "data": [
        {
            "id": "1",
            "name": "List one"
        },
        {
            "id": "2",
            "name": "List two"
        }
    ]
}
```

---

### Cadastrar Lead
Faz registro do Lead

#### Requisição:

```GET /lead```

#### Parâmetros
 - ```list``` - ID da Lista.
 - ```email``` - E-mail do lead.
 - ```whatsapp``` - Número do WhatsApp do lead (opcional).

#### Resposta:

```json
{
    "code": "202",
    "data": {
        "message": "ok"
    }
}
```

---

# Script de Formulários

Instale antes do fechamdno do ```</head>``` o seguinte script:

```html
    <!-- Leads Tática de Sucesso -->
    <script src="//leads.taticadesucesso.com.br/out_form.js"></script>
```

E logo apóst você declarar seu formulário (ou seja: depois do ```</form>```), chame a função ```form_lead(class, callback)```, como no exemplo a seguir:

```html
    <script>
    form_lead('.class_do_form', function(d){

        jQuery('.class_do_form button')
            .attr("disabled","disabled")
            .text('Enviado!');

        jQuery('.class_do_form input').fadeOut('fast');

        //Facebook Pixel
        fbq('track', 'Lead', {
            list: 'Gatilhos Mentais'
        });
  

    });
    </script>
```
Onde ```.class_do_form``` é a classe no formulário. Os campos desse formulário devem respeitar os mesmos nomes dos parâmetros do [Cadastro de Lead](#cadastrar-lead).


---

# Autor

Esse API REST de PHP foi desenvolvido por Tihh Gonçalves (tiago@tiago.art.br).
 
![logo](https://raw.githubusercontent.com/tihhgoncalves/tihh.cliente.jpc.api-doc/master/logo.png)

Mais informações: www.tiago.art.br
