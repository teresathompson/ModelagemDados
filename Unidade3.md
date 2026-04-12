# 📘 Descrição detalhada dos elementos do DER (Modelo Chen)

## 🔷 Entidade

A entidade representa um objeto do mundo real (físico ou abstrato) sobre o qual desejamos armazenar informações. Pode ser uma pessoa, lugar, evento ou conceito. Cada entidade possui um conjunto de atributos que descrevem suas características.

---

## 🔷 Entidade fraca

A entidade fraca é aquela que não possui uma chave primária própria suficiente para identificá-la unicamente. Sua existência depende de uma entidade forte, sendo identificada por meio de um relacionamento com esta, geralmente chamado de relacionamento identificador.

---

## 🔷 Relacionamento

O relacionamento representa a associação entre duas ou mais entidades. Ele indica como os dados de uma entidade estão conectados com os de outra no contexto do sistema.

---

## 🔷 Relacionamento identificador

É um tipo especial de relacionamento que vincula uma entidade fraca à sua entidade forte. Ele é responsável por garantir a identificação única da entidade fraca, complementando sua chave.

---

## 🔷 Atributo

O atributo corresponde a uma propriedade ou característica de uma entidade ou relacionamento. Ele descreve detalhes específicos, como nome, idade, data ou valor.

---

## 🔷 Atributo chave

É o atributo (ou conjunto de atributos) responsável por identificar de forma única cada instância de uma entidade. Também é conhecido como chave primária.

---

## 🔷 Atributo multivalorado

Representa um atributo que pode possuir múltiplos valores para uma mesma entidade. Por exemplo, uma pessoa pode ter vários números de telefone.

---

## 🔷 Atributo derivado

É um atributo cujo valor pode ser calculado a partir de outros atributos. Ele não precisa ser armazenado diretamente no banco de dados, pois pode ser obtido por meio de processamento.

---

## 🔷 Atributo composto

É um atributo que pode ser subdividido em partes menores, cada uma com significado próprio. Por exemplo, um endereço pode ser composto por rua, número, cidade e CEP.

---

## 🔷 Participação total

Indica que todas as instâncias de uma entidade participam obrigatoriamente de um relacionamento. Ou seja, não pode existir uma ocorrência da entidade sem estar associada ao relacionamento.

---

## 🔷 Cardinalidade (1:N)

Define a quantidade de ocorrências de uma entidade que podem estar relacionadas com outra. No caso 1:N, uma instância de uma entidade pode se relacionar com várias da outra, mas o inverso não ocorre.

---

## 🔷 Restrição estrutural (mín, máx)

Especifica os limites mínimo e máximo de participação de uma entidade em um relacionamento, tornando a modelagem mais precisa e controlada.

```mermaid

flowchart LR
    ENTIDADE[📦 Entidade]

    ATR1([Atributo])
    ATR2([🔑 Atributo Chave])
    ATR3([📚 Multivalorado])
    ATR4([⚙️ Derivado])

    ENTIDADE --- ATR1
    ENTIDADE --- ATR2
    ENTIDADE --- ATR3
    ENTIDADE --- ATR4

    classDef entidade fill:#BBDEFB,stroke:#0D47A1,stroke-width:2px,color:#000;
    classDef atributo fill:#E1BEE7,stroke:#6A1B9A,stroke-width:1.5px,color:#000;

    class ENTIDADE entidade;
    class ATR1,ATR2,ATR3,ATR4 atributo;
```

```mermaid


flowchart TD
    ENDERECO([📍 Endereço])

    RUA([Rua])
    NUMERO([Número])
    CIDADE([Cidade])
    CEP([CEP])

    ENDERECO --- RUA
    ENDERECO --- NUMERO
    ENDERECO --- CIDADE
    ENDERECO --- CEP

    classDef composto fill:#FFE0B2,stroke:#E65100,stroke-width:2px,color:#000;
    classDef sub fill:#FFF3E0,stroke:#FB8C00,stroke-width:1px,color:#000;

    class ENDERECO composto;
    class RUA,NUMERO,CIDADE,CEP sub;
```

```mermaid

flowchart LR
    E1[Entidade 1]
    E2[Entidade 2]

    R{Relacionamento}

    E1 --- R
    R --- E2

    classDef entidade fill:#C8E6C9,stroke:#1B5E20,stroke-width:2px,color:#000;
    classDef rel fill:#FFF9C4,stroke:#F57F17,stroke-width:2px,color:#000;

    class E1,E2 entidade;
    class R rel;

```

```mermaid
flowchart LR
    FORTE[Entidade Forte]
    FRACA[[Entidade Fraca]]

    REL{{Relacionamento Identificador}}

    FORTE --- REL
    REL --- FRACA

    classDef forte fill:#BBDEFB,stroke:#0D47A1,stroke-width:2px,color:#000;
    classDef fraca fill:#FFCDD2,stroke:#B71C1C,stroke-width:2px,color:#000;
    classDef rel fill:#FFF59D,stroke:#F57F17,stroke-width:2px,color:#000;

    class FORTE forte;
    class FRACA fraca;
    class REL rel;
```

```mermaid
flowchart LR
    E1[Entidade 1]
    E2[Entidade 2]

    R{Relacionamento}

    E1 -- "1" --- R
    R -- "N" --- E2

    classDef entidade fill:#E3F2FD,stroke:#1565C0,stroke-width:2px,color:#000;
    classDef rel fill:#FFF3E0,stroke:#EF6C00,stroke-width:2px,color:#000;

    class E1,E2 entidade;
    class R rel;
```

```mermaid
flowchart LR
    E[Entidade]
    R{"Relacionamento<br/>(min,max)"}

    E --- R

    classDef entidade fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px,color:#000
    classDef rel fill:#FFFDE7,stroke:#F9A825,stroke-width:2px,color:#000

    class E entidade
    class R rel
```
