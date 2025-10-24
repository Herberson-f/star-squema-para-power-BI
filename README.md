# star-squema-para-power-BI

# Desafio de Modelagem Dimensional – Star Schema (Foco no Professor)

## 🎯 Objetivo
Criar um **modelo dimensional (Star Schema)** com base no **modelo relacional** fornecido.  
O objetivo é permitir **análises focadas no professor**, contemplando suas disciplinas, cursos e locais de atuação.

---

## 🧩 Contexto do Modelo
O modelo relacional original apresenta as seguintes entidades principais:
- **Aluno**
- **Professor**
- **Curso**
- **Disciplina**
- **Campus**
- **Tempo**
- **Avaliação Geral** (tabela central de relacionamento entre as demais)

A partir desse modelo, foi construída uma estrutura dimensional simplificada com foco analítico.

---

## 🌟 Modelo Dimensional Proposto

### 🧮 **Tabela Fato: `Fato_AvaliacaoProfessor`**
Contém os indicadores e métricas relacionados ao desempenho e atividades do professor.

**Atributos principais:**
- `id_fato_avaliacao`
- `id_professor`
- `id_disciplina`
- `id_curso`
- `id_tempo`
- `id_campus`
- `media_nota`
- `qtd_turmas`
- `qtd_avaliacoes`
- `qtd_aprovacoes`
- `qtd_reprovacoes`

> A tabela fato representa o evento analisável — **a avaliação do professor** em suas disciplinas, cursos e períodos.

---

### 📊 **Tabelas Dimensão**

#### 1. `Professor`
- `id_professor`
- `nome_professor`
- `departamento`
- `formacao`
- `tempo_casa`
- `titulacao`

#### 2. `Disciplina`
- `id_disciplina`
- `nome_disciplina`
- `carga_horaria`
- `nivel`

#### 3. `Curso`
- `id_curso`
- `nome_curso`
- `modalidade`
- `area_conhecimento`

#### 4. `Campus`
- `id_campus`
- `nome_campus`
- `cidade`
- `estado`

#### 5. `Tempo`
- `id_tempo`
- `data`
- `dia`
- `mes`
- `ano`
- `semestre`

> A dimensão tempo foi criada para compensar a falta de informações temporais detalhadas no modelo relacional, permitindo análises por períodos.

---

## 🔁 Relacionamentos (Esquema em Estrela)

```
                  Dim_Tempo
                      |
Dim_Curso — Fato_AvaliacaoProfessor — Dim_Professor
                      |
               Dim_Disciplina
                      |
                 Dim_Campus
```

Cada dimensão conecta-se diretamente à tabela fato por meio de suas chaves primárias.

---

## 🧠 Observações Importantes
- O modelo foi **centralizado no professor**, sendo ele o principal objeto de análise.  
- O **aluno não foi considerado** neste modelo, conforme as instruções do desafio.  
- A **granularidade temporal** pode variar (ex: diária, mensal ou semestral), conforme os dados disponíveis.  
- Esse esquema permite análises como:
  - Média de notas por professor, disciplina e período.
  - Comparativo de desempenho entre professores.
  - Quantidade de turmas e avaliações ministradas por curso/campus.

---

## 🧾 Autor e Entrega
**Desafio de Modelagem Dimensional – Faculdade (Foco no Professor)**  
Desenvolvido como parte de estudo de **modelagem dimensional e BI**.
