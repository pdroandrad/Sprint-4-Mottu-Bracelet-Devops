# Mottu Bracelet

## 📌 Descrição do Projeto

O **Mottu Bracelet** é um projeto desenvolvido para a empresa Mottu, visando o gerenciamento eficiente de motos nos pátios de manutenção. Cada moto recebe um bracelete que se comunica com o aplicativo, permitindo:

- Localização rápida da moto no pátio.
- Emissão de sinais sonoros e infravermelhos acionados pelo dispositivo.
- Integração de informações entre moto, pátio e dispositivo.

Esta versão do projeto implementa uma **API RESTful** utilizando **ASP.NET Core Web API**, com foco em boas práticas:

- Endpoints CRUD para as entidades **Moto**, **Dispositivo**, **Patio** e **HistoricoPatio**.
- Paginação em listagens.
- Suporte a **HATEOAS** (links para navegação entre recursos).
- Status codes HTTP adequados.
- Documentação automática via **Swagger/OpenAPI**.
---

## 👨‍💻 Integrantes

- Pedro Abrantes Andrade | RM558186
- Ricardo Tavares de Oliveira Filho | RM556092
- Victor Alves Carmona | RM555726

---

## 🚀 Tecnologias Utilizadas

- ASP.NET Core 8.0 Web API  
- C#  
- Entity Framework Core  
- Banco de Dados Oracle  
- Swagger / OpenAPI  
- JSON  
- Visual Studio 2022 ou superior  

---

## 📂 Instalação e Execução

### Pré-requisitos

- .NET 8.0 ou superior  
- Visual Studio 2022 ou superior  
- Acesso ao banco de dados Oracle com usuário e senha válidos  

### Executando o projeto

1. Clone o repositório:

   ```
   git clone https://github.com/pdroandrad/Sprint-3-Mottu-Bracelet-CSharp
   ```

2. Abra o projeto no Visual Studio.

3. Verifique se a string de conexão no `appsettings.json` está correta:

  ```
  "ConnectionStrings": {
  "DefaultConnection": "Data Source=oracle.fiap.com.br:1521/orcl; User Id='seu-usuario'; Password='sua-senha';"
}
```

4. Rode a aplicação clicando no botão de execução com o protocolo HTTPS selecionado. O Swagger será iniciado automaticamente com os endpoints disponíveis.

### 💡 Justificativa das Entidades

Escolhemos estas entidades para representar o domínio do sistema MottuBracelet de forma completa:

- **Moto:** representa cada moto que entra no pátio e precisa ser rastreada.
- **Dispositivo:** representa o bracelete acoplado à moto, responsável por sinais sonoros e infravermelhos.
- **Patio:** representa os locais onde as motos são armazenadas ou mantidas.
- **HistoricoPatio:** registra os movimentos das motos entre pátios, garantindo rastreabilidade e integridade dos dados.

Essas entidades permitem um modelo consistente para gerenciar operações de localização, manutenção e histórico de forma eficiente.

## 📡 Endpoints da API

### 🔧 MotoController

| Método | Endpoint             | Descrição                                        |
|--------|----------------------|--------------------------------------------------|
| GET    | `/api/Moto`          | Retorna todas as motos com paginação.           |
| GET    | `/api/Moto/{id}`     | Retorna uma moto específica por ID com links HATEOAS. |
| POST   | `/api/Moto`          | Cria uma nova moto e associa ao dispositivo informado. |
| PUT    | `/api/Moto/{id}`     | Atualiza uma moto existente.                    |
| DELETE | `/api/Moto/{id}`     | Remove uma moto do sistema.                     |

---

### 🔧 DispositivoController

| Método | Endpoint                  | Descrição                                         |
|--------|---------------------------|--------------------------------------------------|
| GET    | `/api/Dispositivo`        | Lista todos os dispositivos com paginação.       |
| GET    | `/api/Dispositivo/{id}`   | Retorna um dispositivo específico por ID com HATEOAS. |
| POST   | `/api/Dispositivo`        | Cria um novo dispositivo.                        |
| PUT    | `/api/Dispositivo/{id}`   | Atualiza as informações de um dispositivo existente. |
| DELETE | `/api/Dispositivo/{id}`   | Remove um dispositivo.                           |

---

### 🔧 PatioController

| Método | Endpoint             | Descrição                                         |
|--------|----------------------|--------------------------------------------------|
| GET    | `/api/Patio`         | Retorna todos os pátios cadastrados com paginação. |
| GET    | `/api/Patio/{id}`    | Retorna um pátio específico por ID com links HATEOAS. |
| POST   | `/api/Patio`         | Cria um novo pátio.                              |
| PUT    | `/api/Patio/{id}`    | Atualiza informações de um pátio existente.      |
| DELETE | `/api/Patio/{id}`    | Remove um pátio do sistema.                      |

---

### 🔧 HistoricoPatioController

| Método | Endpoint                    | Descrição                                                |
|--------|-----------------------------|----------------------------------------------------------|
| GET    | `/api/HistoricoPatio`       | Lista todos os registros de histórico com paginação.    |
| GET    | `/api/HistoricoPatio/{id}`  | Retorna um registro de histórico específico por ID com links HATEOAS. |
| POST   | `/api/HistoricoPatio`       | Cria um novo registro de movimentação de moto entre pátios. |


## 📦 Exemplos de Payloads

> **Observação:** Para respeitar os relacionamentos entre as tabelas, crie os objetos na seguinte ordem:  
> `Patio` → `Dispositivo` → `Moto` → `HistoricoPatio`

### 🔹 Patio

**POST /api/Patio**

```json
{
  "nome": "Patio Central",
  "endereco": "Rua das Flores, 123"
}
```

**PUT /api/Patio/{id}**

```json
{
  "nome": "Patio Leste",
  "endereco": "Avenida das Palmeiras, 456"
}
```

### 🔹 Dispositivo

**POST /api/Dispositivo**

```json
{
  "codigo": "BR-001",
  "status": "Ativo"
}
```

**PUT /api/Dispositivo/{id}**

```json
{
  "codigo": "BR-002",
  "status": "Inativo"
}
```

### 🔹 Moto

**POST /api/Moto**

```json
{
  "imei": "123456789012345",
  "placa": "ABC-1234",
  "dispositivoId": 1
}
```

**PUT /api/Moto/{id}**

```json
{
  "imei": "987654321098765",
  "placa": "XYZ-9876",
  "dispositivoId": 1
}
```

### 🔹 HistoricoPatio

**POST /api/HistoricoPatio**

```json
{
  "motoId": 1,
  "patioId": 2,
  "dataMovimentacao": "2025-09-18T10:00:00"
}
```
