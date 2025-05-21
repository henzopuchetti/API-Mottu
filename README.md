
# 🏍️ Mottu Pátio - API de Controle Automatizado de Motos

## 📘 Descrição do Projeto

Este projeto é uma API REST desenvolvida em Java com Spring Boot para automatizar o controle de entrada, saída e posicionamento de motocicletas nos pátios da Mottu. A solução tem como objetivo eliminar processos manuais e tornar a gestão dos pátios mais eficiente, segura e escalável.

---

## ❗ Problema

A Mottu gerencia centenas de motos em pátios espalhados pelo Brasil e México. O controle atual, feito de forma manual por operadores, é suscetível a falhas humanas, dificulta a localização das motos e compromete a produtividade. Além disso, a ausência de rastreabilidade e visibilidade em tempo real impacta diretamente a operação e a experiência dos entregadores.

---

## ✅ Solução

A API proposta integra um sistema com tecnologia de **Leitura Automática de Placas (LPR)** e uma **plataforma web** que permite:

- Registro automático da entrada e saída de motos;
- Mapeamento e rastreamento das vagas em tempo real;
- Visibilidade completa da situação dos pátios;
- Integração com o sistema interno da Mottu para vincular motos a operadores.

---

## 🛠️ Tecnologias Utilizadas

- **Java 17**
- **Spring Boot 3.4.5**
  - Spring Web
  - Spring Data JPA
  - Bean Validation
  - Spring Cache
- **Banco de Dados H2 (em memória)**
- **Lombok**
- **MapStruct**
- **Maven**

---

## 📁 Estrutura de Pacotes

```
com.fiap.mottu_patio
├── config
├── controller
├── dto
├── exception
├── mapper
├── model
├── repository
├── service
└── specification
```

---

## 🔌 Endpoints Principais
---

## 🧪 Exemplos de Requisições (via Postman)

### 📦 Pátios

#### POST `/api/patios`
```json
{
  "nome": "Patio da VP",
  "endereco": "Rua das Flores, 123",
  "capacidade": 30
}
```

#### GET `/api/patios`
```http
http://localhost:8080/api/patios
```

---

### 🧠 Vagas

#### GET `/vagas/patio/1/formatado`
```http
http://localhost:8080/vagas/patio/1/formatado
```

---

### 🏍️ Motos

#### POST `/api/motos`
```json
{
  "placa": "ABC1234",
  "modelo": "Honda azul",
  "cor": "azul",
  "ano": 2025,
  "patioId": 1
}
```

#### GET `/api/motos`
```http
http://localhost:8080/api/motos
```

---

### 📷 Eventos LPR

#### POST `/api/eventosLPR` (Entrada)
```json
{
  "tipoEvento": "ENTRADA",
  "placa": "ABC1234",
  "vaga": "A:1"
}
```

#### POST `/api/eventosLPR` (Saída)
```json
{
  "tipoEvento": "SAIDA",
  "placa": "ABC1234"
}
```


### 📦 Motos (`/api/motos`)
- `POST` - Criar moto
- `GET` - Listar todas
- `GET /{id}` - Buscar por ID
- `PUT /{id}` - Atualizar
- `DELETE /{id}` - Deletar

### 🏟️ Pátios (`/api/patios`)
- `POST` - Criar pátio (com geração automática de vagas)
- `GET` - Listar todos
- `GET /{id}` - Buscar por ID
- `PUT /{id}` - Atualizar (inclusive vagas)
- `DELETE /{id}` - Deletar

### 🧠 Eventos LPR (`/api/eventosLPR`)
- `POST` - Registrar entrada/saída da moto via placa
- `GET` - Listar com filtros por tipo, placa e paginação
- `GET /{id}` - Buscar por ID
- `PUT /{id}` - Atualizar evento
- `DELETE /{id}` - Remover evento

### 📊 Vagas (`/vagas/patio/{id}/formatado`)
- `GET` - Ver vagas agrupadas por fileira e ocupação

---

## ⚙️ Como Rodar o Projeto

### Pré-requisitos:
- Java 17 instalado
- Maven instalado

### Passos:

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/mottu-patio.git
cd mottu-patio

# Compile o projeto
mvn clean install

# Rode a aplicação
mvn spring-boot:run
```

A API estará disponível em:  
📍 `http://localhost:8080`

---

## 🧠 Futuras Melhorias

- ✅ **Implementar autenticação e autorização** para controle de acesso à API;
- ✅ **Criar dashboard visual** com Spring + React para supervisão dos pátios em tempo real;
- ✅ **Integrar com API externa de leitura de motos** (fornecida pela Mottu ou terceiros) para automatizar o processo de entrada e saída, substituindo o envio manual da placa via request.

