## Entidades

As entidades são os principais elementos da modelagem Entidade-Relacionamento. Elas representam coisas do mundo real sobre as quais queremos guardar informações.

Uma entidade pode ser uma pessoa, um objeto, um lugar ou até mesmo um conceito. O importante é que ela possa ser identificada e descrita dentro do sistema.

De forma simples, pense assim: **entidade é tudo aquilo que você quer cadastrar no sistema**.

Por exemplo, em um sistema de hospital, algumas entidades podem ser **Médicos** e **Pacientes**, pois queremos armazenar informações sobre eles e entender como eles se relacionam (como atendimentos, consultas, etc.).

## Exemplos de entidade e instâncias

<br>
<br>

```mermaid
flowchart LR
    A[Aluno]

    I1[Marina Silva]
    I2[Carlos Cunha]
    I3[Maria José]
    I4[José Silva]

    A --> I1
    A --> I2
    A --> I3
    A --> I4


```

##

```mermaid

flowchart LR
    A[Animal]

    I1[Gato 🐱]
    I2[Cachorro 🐶]
    I3[Coelho 🐰]
    I4[Panda 🐼]
    I5[Hamster 🐹]

    A --> I1
    A --> I2
    A --> I3
    A --> I4
    A --> I5
```

## Relacionamentos

<br>

```mermaid
flowchart LR


    %% ENTIDADES
    MEDICO[Médico] --- ATENDIMENTO{Atendimento}
    PACIENTE[Paciente] --- ATENDIMENTO
    ATENDIMENTO --- HOSPITAL[Hospital]


    %% ESTILOS
    classDef entidade fill:#E3F2FD,stroke:#1E88E5,stroke-width:2px,color:#000;
    classDef relacionamento fill:#FFF3E0,stroke:#FB8C00,stroke-width:2px,color:#000;

    class MEDICO,PACIENTE,HOSPITAL entidade;
    class ATENDIMENTO relacionamento;
```

```mermaid
flowchart LR
    %% ENTIDADES
    PROFESSOR[Professor]
    DISCIPLINA[Disciplina]

    %% RELACIONAMENTO
    MINISTRA{Ministra}

    %% CONEXÕES
    PROFESSOR --- MINISTRA ---  DISCIPLINA

    %% ESTILOS
    classDef entidade fill:#E8F5E9,stroke:#43A047,stroke-width:2px,color:#000;
    classDef relacionamento fill:#FFF8E1,stroke:#F9A825,stroke-width:2px,color:#000;

    class PROFESSOR,DISCIPLINA entidade;
    class MINISTRA relacionamento;
```

```mermaid
flowchart LR
    VETERINARIO[👩‍⚕️ Veterinário] --- CONSULTA{🩺 Consulta} --- ANIMAL[🐶 Animal]
```

## Cardinalidade: Relacionamento 1:1 (Um para Um)

Um relacionamento **um para um (1:1)** ocorre quando cada instância de uma entidade está associada a apenas uma instância de outra entidade, e vice-versa.

- Cada **🧑 pessoa** possui **📞 um telefone**
- Cada **📞 telefone** pertence a **🧑 uma pessoa**

👉 Ou seja:  
**1 pessoa ⇄ 1 telefone**

> [!CAUTELA]
> Avalie cada regra de negócios. Hoje em dia cada pessoa pode possuir mais do que um telefone, mas para este exemplo o relacionamento era de 1:1.

### Exemplo: Pessoa e Telefone

```mermaid
flowchart LR
    PESSOA[🧑 Vendedor] --- POSSUI{📱 Possui} --- TELEFONE[📞 Telefone]

    %% Estilo
    classDef entidade fill:#E1F5FE,stroke:#0288D1,stroke-width:2px,color:#000;
    classDef relacionamento fill:#FFF3E0,stroke:#FB8C00,stroke-width:2px,color:#000;

    class PESSOA,TELEFONE entidade;
    class POSSUI relacionamento;
```

## Cardinalidade: Relacionamento Muitos para Muitos (M:N)

```mermaid
flowchart LR
    %% ALUNOS
    A1[👩‍🎓 Ana]
    A2[👨‍🎓 Bruno]
    A3[👩‍🎓 Carla]
    A4[👨‍🎓 Diego]

    %% DISCIPLINAS
    D1[📘 Matemática]
    D2[🧪 Física]
    D3[🎨 Artes]
    D4[💻 Programação]

    %% RELACIONAMENTO
    MATRICULA{📚 Matrícula}

    %% CONEXÕES ALUNOS → RELACIONAMENTO
    A1 --- MATRICULA
    A2 --- MATRICULA
    A3 --- MATRICULA
    A4 --- MATRICULA

    %% CONEXÕES RELACIONAMENTO → DISCIPLINAS
    MATRICULA --- D1
    MATRICULA --- D2
    MATRICULA --- D3
    MATRICULA --- D4

    %% ESTILOS
    classDef aluno fill:#E3F2FD,stroke:#1E88E5,stroke-width:2px,color:#000;
    classDef disciplina fill:#E8F5E9,stroke:#43A047,stroke-width:2px,color:#000;
    classDef relacionamento fill:#FFF3E0,stroke:#FB8C00,stroke-width:2px,color:#000;

    class A1,A2,A3,A4 aluno;
    class D1,D2,D3,D4 disciplina;
    class MATRICULA relacionamento;
```

## Cardinalidade: Relacionamento Um para Muitos (1:N)

```mermaid
flowchart LR
    %% RESPONSÁVEIS
    R1[👩 Responsável Ana]
    R2[👨 Responsável João]

    %% ALUNOS
    A1[👧 Maria]
    A2[👦 Pedro]
    A3[👧 Sofia]
    A4[👦 Lucas]

    %% RELACIONAMENTOS (separados!)
    REL1{👨‍👩‍👧 Responsável por}
    REL2{👨‍👩‍👧 Responsável por}

    %% CONEXÕES CORRETAS
    R1 --- REL1
    REL1 --- A1
    REL1 --- A2

    R2 --- REL2
    REL2 --- A3
    REL2 --- A4

    %% ESTILO
    classDef responsavel fill:#E3F2FD,stroke:#1E88E5,stroke-width:2px,color:#000;
    classDef aluno fill:#E8F5E9,stroke:#43A047,stroke-width:2px,color:#000;
    classDef relacionamento fill:#FFF3E0,stroke:#FB8C00,stroke-width:2px,color:#000;

    class R1,R2 responsavel;
    class A1,A2,A3,A4 aluno;
    class REL1,REL2 relacionamento;
```
