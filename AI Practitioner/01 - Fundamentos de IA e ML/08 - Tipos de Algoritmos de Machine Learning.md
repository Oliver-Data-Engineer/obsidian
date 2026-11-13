
## Resumo

Os algoritmos de [[02 - O que é Machine Learning|Machine Learning]] se dividem em **três grandes famílias**, de acordo com a forma como aprendem. Esta nota é o **índice** da pasta de ML.

## Notas desta pasta

| Nota | Em uma frase |
|---|---|
| [[04 - Aprendizado Supervisionado\|Aprendizado Supervisionado]] | Aprende com **dados rotulados** (tem gabarito) para **prever** categorias ou valores. |
| [[05 - Aprendizado Não Supervisionado\|Aprendizado Não Supervisionado]] | Aprende com **dados sem rótulo** para **descobrir** grupos e padrões escondidos. |
| [[06 - Aprendizado por Reforço\|Aprendizado por Reforço]] | Um **agente** aprende por **tentativa e erro**, guiado por **recompensas**. |
| [[07 - Diferenças entre os Tipos de Aprendizado\|Diferenças entre os Tipos de Aprendizado]] | Tabela comparativa, cenários práticos e tipos intermediários. |

🗺️ **Mapa visual:** [[03 - Tipos de Aprendizado de Machine Learning.canvas|Tipos de Aprendizado de Machine Learning]]

## Visão Geral

```mermaid
flowchart TD
    ML[Machine Learning] --> S[Supervisionado<br/>dados rotulados]
    ML --> U[Não Supervisionado<br/>dados sem rótulo]
    ML --> R[Por Reforço<br/>recompensa e punição]
    S --> S1[Classificação]
    S --> S2[Regressão]
    U --> U1[Clusterização]
    U --> U2[Detecção de Anomalias]
    U --> U3[Associação]
    U --> U4[Redução de Dimensionalidade]
    R --> R1[Agente + Ambiente]
    R --> R2[Política / Estratégia]
```

## Exemplo para Associação Mental

- **Supervisionado** = 📘 estudar com o **gabarito**.
- **Não Supervisionado** = 🧦 organizar a **gaveta de meias** sem ninguém dizer como.
- **Por Reforço** = 🐶 **adestrar um cachorro** com petiscos.
