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
