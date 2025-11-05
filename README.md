# Mottu Bracelet

## 📌 Descrição do Projeto

O **Mottu Bracelet** é uma aplicação desenvolvida para auxiliar a empresa **Mottu** no gerenciamento e localização de motos nos pátios de manutenção.  
Cada motocicleta possui um dispositivo (“bracelete”) que permite:

✅ Localização rápida da moto no pátio  
✅ Emissão de alertas sonoros e infravermelhos  
✅ Armazenamento do histórico de movimentações da moto  

A solução expõe uma **API REST em .NET 8**, com integração a um **banco de dados Azure SQL**, e deploy automatizado via **Azure DevOps**, utilizando **Docker** e **Azure**

---

## 👨‍💻 Integrantes

- Pedro Abrantes Andrade | RM558186
- Ricardo Tavares de Oliveira Filho | RM556092
- Victor Alves Carmona | RM555726

---

## 🚀 Tecnologias Utilizadas

- .NET 8 – ASP.NET Web API
- C#
- Entity Framework Core
- Azure SQL Database
- Docker
- Azure DevOps (CI/CD)
- Azure Web App
- Swagger / OpenAPI

---

## 📡 Endpoints da API

### 🔧 Moto

| Método | Endpoint             | Descrição                                        |
|--------|----------------------|--------------------------------------------------|
| GET    | `/api/Moto`          | Retorna todas as motos com paginação.           |
| GET    | `/api/Moto/{id}`     | Retorna uma moto específica por ID com links HATEOAS. |
| POST   | `/api/Moto`          | Cria uma nova moto e associa ao dispositivo informado. |
| PUT    | `/api/Moto/{id}`     | Atualiza uma moto existente.                    |
| DELETE | `/api/Moto/{id}`     | Remove uma moto do sistema.                     |

---

### 🔧 Dispositivo

| Método | Endpoint                  | Descrição                                         |
|--------|---------------------------|--------------------------------------------------|
| GET    | `/api/Dispositivo`        | Lista todos os dispositivos com paginação.       |
| GET    | `/api/Dispositivo/{id}`   | Retorna um dispositivo específico por ID com HATEOAS. |
| POST   | `/api/Dispositivo`        | Cria um novo dispositivo.                        |
| PUT    | `/api/Dispositivo/{id}`   | Atualiza as informações de um dispositivo existente. |
| DELETE | `/api/Dispositivo/{id}`   | Remove um dispositivo.                           |

---

### 🔧 Patio

| Método | Endpoint             | Descrição                                         |
|--------|----------------------|--------------------------------------------------|
| GET    | `/api/Patio`         | Retorna todos os pátios cadastrados com paginação. |
| GET    | `/api/Patio/{id}`    | Retorna um pátio específico por ID com links HATEOAS. |
| POST   | `/api/Patio`         | Cria um novo pátio.                              |
| PUT    | `/api/Patio/{id}`    | Atualiza informações de um pátio existente.      |
| DELETE | `/api/Patio/{id}`    | Remove um pátio do sistema.                      |

---

### 🔧 HistoricoPatio

| Método | Endpoint                    | Descrição                                                |
|--------|-----------------------------|----------------------------------------------------------|
| GET    | `/api/HistoricoPatio`       | Lista todos os registros de histórico com paginação.    |
| GET    | `/api/HistoricoPatio/{id}`  | Retorna um registro de histórico específico por ID com links HATEOAS. |
| POST   | `/api/HistoricoPatio`       | Cria um novo registro de movimentação de moto entre pátios. |


## 📦 Exemplo de Payload para teste

**POST /api/Patio**

```json
{
  "nome": "Patio Central",
  "capacidadeMaxima": 50,
  "administradorResponsavel": "João Silva",
  "endereco": {
    "logradouro": "Rua das Flores",
    "numero": 123,
    "cep": "12345-678",
    "complemento": "Próximo ao supermercado",
    "cidade": "São Paulo",
    "pais": "Brasil"
  }
}
```

**PUT /api/Patio/{id}**

```json
{
  "nome": "Patio Norte",
  "capacidadeMaxima": 100,
  "administradorResponsavel": "João Silva",
  "endereco": {
    "logradouro": "Rua das Flores",
    "numero": 123,
    "cep": "12345-678",
    "complemento": "Próximo ao supermercado",
    "cidade": "São Paulo",
    "pais": "Brasil"
  }
}
```



