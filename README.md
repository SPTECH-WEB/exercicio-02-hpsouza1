
# 📦 Sistema de Cálculo de Frete com Padrões de Projeto

## 🔍 Visão Geral
Projeto Java que implementa:
- **Strategy Pattern** para múltiplas formas de cálculo de frete
- **Adapter Pattern** para integração com API externa
- **Observer Pattern** para notificações

## 🏗️ Diagrama de Componentes
```mermaid
classDiagram
    class FreteController {
        +calcular(Double peso, String modalidade)
    }
    
    class FreteService {
        -List<FreteStrategy> estrategias
        -List<Notificador> notificadores
        +calcularFrete()
    }
    
    interface FreteStrategy {
        <<interface>>
        +calcularFrete(double peso)
        +modalidade() String
    }
    
    class EntregaExpressa {
        +calcularFrete()
        +modalidade()
    }
    
    class EntregaEconomica {
        +calcularFrete()
        +modalidade()
    }
    
    class TransportadoraTercerizadaAdapter {
        -APIExternaTransportadora apiExterna
        +calcularFrete()
        +modalidade()
    }
    
    class APIExternaTransportadora {
        +calculoExterno(double peso)
    }
    
    interface Notificador {
        <<interface>>
        +notificar(String mensagem)
    }
    
    class EmailNotificador {
        +notificar(String mensagem)
    }
    
    FreteController --> FreteService
    FreteService --> FreteStrategy
    FreteService --> Notificador
    FreteStrategy <|-- EntregaExpressa
    FreteStrategy <|-- EntregaEconomica
    FreteStrategy <|-- TransportadoraTercerizadaAdapter
    TransportadoraTercerizadaAdapter --> APIExternaTransportadora
    Notificador <|-- EmailNotificador