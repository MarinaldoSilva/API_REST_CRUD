<div align="center">
<h1># API_REST_CRUD</h1>
<p>Estudo e treinamento sobre API_REST no padrão RESTful, onde será criado um CRUD para treinamento dos conceitos aqui aprendidos.</p>
</div>

<br>

<div align="center">
<h1>Desvendando o Mundo das APIs REST</h1>
<p>Um guia sobre os principais conceitos e práticas</p>
</div>

---

### 1. 🌐 REST: Transferência Representacional de Estado

* <p align="left"> <img src="https://img.icons8.com/color/48/000000/api-interface.png" width="20px" alt="API Icon"/> **API:** Uma interface que permite a comunicação entre diferentes sistemas de software.</p>
* <p align="left"> <img src="https://img.icons8.com/color/48/000000/rest-api.png" width="20px" alt="REST Icon"/> **REST vs. RESTful:** REST é um conjunto de princípios arquiteturais. Uma API é considerada **RESTful** quando segue essas regras para sua criação.</p>

---

### 2. 🎯 Endpoints (Substantivos)

Os **Endpoints** são os "substantivos" da sua API. Eles representam a lógica de negócio e os recursos que você manipula.

* **Exemplo:** `/produtos`, `/categorias`

#### Tipos de Endpoints:

* <p align="left"> <img src="https://img.icons8.com/color/48/000000/shopping-cart.png" width="20px" alt="Coleção Icon"/> **Endpoints de Coleção:** Acessam um conjunto de recursos.</p>
  `URL/api/v1/produtos`
  <br>
  *(Acessando uma coleção inteira de produtos.)*

* <p align="left"> <img src="https://img.icons8.com/color/48/000000/shopping-bag.png" width="20px" alt="Individual Icon"/> **Endpoints Individuais:** Acessam um recurso específico.</p>
  `URL/api/v1/produtos/42`
  <br>
  *(Acessando um produto específico com o ID 42.)*

> **Dica:** Utilize substantivos no plural (`/produtos`) e mantenha a consistência.

---

### 3. 🚦 Endpoints (Verbos HTTP)

Os **verbos HTTP** indicam a ação que você deseja realizar em um recurso.

* `POST` <img src="https://img.icons8.com/color/48/000000/add-file.png" width="20px" alt="POST Icon"/> - **CRIAR**
* `GET` <img src="https://img.icons8.com/color/48/000000/get-data.png" width="20px" alt="GET Icon"/> - **LER / BUSCAR**
* `PUT` <img src="https://img.icons8.com/color/48/000000/edit-file.png" width="20px" alt="PUT Icon"/> - **ATUALIZAR**
* `DELETE` <img src="https://img.icons8.com/color/48/000000/delete-file.png" width="20px" alt="DELETE Icon"/> - **APAGAR**

#### Utilização Correta:

| Verbo   | Uso         | URL               | Descrição                                                                 |
| :------ | :---------- | :---------------- | :------------------------------------------------------------------------ |
| **GET** | Ler         | `/api/produtos` <br> `/api/produtos/42` | Busca uma coleção ou um item específico. |
| **POST** | Criar       | `/api/produtos`   | **Correto:** Adiciona um novo item à coleção. <br>**Erro:** Não use com um ID. |
| **PUT** | Atualizar   | `/api/produtos/42` | **Correto:** Atualiza um item específico. <br>**Erro:** Necessita de um ID. |
| **DELETE**| Apagar      | `/api/produtos/42` | **Correto:** Remove um item específico. <br>**Erro:** Necessita de um ID. |

---

### 4. 📩 Request (Requisição)

A requisição é a solicitação que o cliente (navegador, aplicativo) envia para o servidor.

#### **Query String**

A `query string` é utilizada para filtrar, ordenar ou limitar os dados de uma requisição `GET`.

* **Exemplo:** `/api/v1/produtos?order=desc&limit=10`
* `?` **(question mark):** Inicia a query string.
* `order=desc`: Par **chave-valor** para personalizar a busca.
* `&` **(e comercial):** Usado para separar múltiplos pares de chave-valor.

#### **Header da Requisição**

O cabeçalho (`Header`) da requisição contém metadados importantes sobre o que o cliente espera receber.

* `Accept`: Indica o tipo de arquivo desejado (e.g., `application/json`, `application/pdf`).
* `Accept-Language`: Informa a língua preferida para a resposta.
* `Cache-Control`: Especifica como e por quanto tempo a resposta pode ser armazenada em cache.

---

### 5. 📨 Response (Resposta)

A resposta é o retorno do servidor após processar a requisição. A resposta deve ser coerente com a requisição e com o status da operação.

#### **Header da Resposta**

A resposta também tem um cabeçalho que contém informações cruciais sobre os dados enviados.

* `Content-type`: O tipo de conteúdo da resposta (e.g., `application/json`).
* `Last-Modified`: Data e hora da última modificação do recurso.
* `Expires`: Data e hora em que a resposta deve ser considerada obsoleta pelo cache.

#### **HTTP Status Codes**

O status code informa o resultado da requisição. Ele é dividido em 5 níveis:

| Código | Nível | Significado | Exemplo |
| :--- | :--- | :--- | :--- |
| `2xx` | **Sucesso** | A requisição foi processada com sucesso. | `200 OK` |
| `3xx` | **Redirecionamento** | A requisição foi entendida, mas o recurso está em outro local. | `301 Moved Permanently` |
| `4xx` | **Erro do Cliente** | A requisição está incorreta. | `404 Not Found` |
| `5xx` | **Erro do Servidor** | O servidor falhou ao processar uma requisição válida. | `500 Internal Server Error` |

> **Observação:** É responsabilidade do desenvolvedor informar o `status http` correto para os clientes da API.

---

### 6. 🛡️ Segurança e Disponibilidade

Para construir APIs robustas, é essencial focar em performance e segurança.

* **Cache:** Utilizar cache (em memória, banco de dados, etc.) para armazenar dados frequentemente acessados. Isso melhora a velocidade e reduz a carga no banco de dados principal. Bancos de dados como **Redis** <img src="https://img.icons8.com/color/48/000000/redis.png" width="20px" alt="Redis Icon"/> são excelentes para esse fim.

* **Limite de Requisições:** Limitar o número de requisições por cliente (`Rate Limiting`) para evitar sobrecarga no servidor, garantindo a disponibilidade do serviço.

* **Autenticação e Autorização:**
    * **Autenticação:** O cliente se identifica. Tokens (como JWT) são a forma mais comum de autenticação em APIs, garantindo que as requisições sejam feitas por usuários válidos, já que o HTTP é **stateless** (sem estado).
    * **Autorização:** Define o que o cliente pode fazer. Após a autenticação, a autorização determina quais verbos HTTP (`GET`, `POST`, `DELETE`, etc.) e quais recursos o cliente tem permissão para acessar.
