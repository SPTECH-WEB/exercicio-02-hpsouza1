# 📦 Sistema de Cálculo de Frete com Padrões de Projeto

## 🔍 Visão Geral
Projeto Java que implementa três padrões de projeto principais:
1. **Strategy**: Para diferentes algoritmos de cálculo de frete
2. **Adapter**: Para integração com API externa de transportadora
3. **Observer**: Para sistema de notificações

## 🏗️ Estrutura dos Componentes

### 1. Componentes Principais
- **FreteController** (Ponto de entrada REST)
  - Recebe requisições HTTP
  - Parâmetros: `peso` (Double) e `modalidade` (String)
  - Delega cálculos para o `FreteService`

- **FreteService** (Núcleo do sistema)
  - Gerencia estratégias de cálculo (Strategy)
  - Administra notificadores (Observer)
  - Contém:
    - Lista de estratégias (`EntregaExpressa`, `EntregaEconomica`, `TransportadoraTercerizadaAdapter`)
    - Lista de notificadores (`EmailNotificador`)

### 2. Hierarquia de Estratégias (Strategy Pattern)
**Interface Base:**
```java
public interface FreteStrategy {
    double calcularFrete(double peso);
    String modalidade();
}