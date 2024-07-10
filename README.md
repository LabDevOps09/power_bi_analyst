# power_bi_analyst

Repositório relacionado a formação de Power BI Analyst

# Desafio de Power BI - Relatório Financeiro

- Importação de dados de vendas a partir de arquivos CSV.
- Criação de layouts de relatórios eficazes, incluindo grids, caixas de texto e imagens.
- Desenvolvimento de gráficos e visualizações de dados significativas com base nos dados de amostra fornecidos.
- Implementação de botões de navegação para facilitar a alternância entre páginas e visuais diferentes.
- Uso de segmentadores de dados para permitir a interação dos usuários com o relatório.
- Publicação do relatório no Power BI Service para compartilhamento online.
- Uso Personalizações avançadas, como ações personalizadas nos botões.


![Capturar](https://github.com/LabDevOps09/power_bi_analyst/assets/166772912/e1d167aa-f550-4b34-8b2f-40360e9e0be4)
![Capturar1](https://github.com/LabDevOps09/power_bi_analyst/assets/166772912/c35586a4-17d8-4f47-a1ce-8a2ce3384ccd)

# Desafio modelagem dimensional

![diagrama](https://github.com/LabDevOps09/power_bi_analyst/assets/166772912/b8aca282-97a6-47a3-b31c-591a66c918df)


<h5> Linhas de código:</h5>

```CREATE TABLE DimensaoProfessor (
    ProfessorID INT PRIMARY KEY,
    Nome VARCHAR(100),
    Titulacao VARCHAR(50),
    Idade INT,
    Sexo VARCHAR(10),
    DataContratacao DATE
);

 CREATE TABLE DimensaoCurso (
    CursoID INT PRIMARY KEY,
    NomeCurso VARCHAR(100),
    Descricao TEXT,
    CargaHoraria INT
);

CREATE TABLE DimensaoDepartamento (
    DepartamentoID INT PRIMARY KEY,
    NomeDepartamento VARCHAR(100),
    ChefeDepartamento VARCHAR(100)
);

CREATE TABLE DimensaoData (
    DataID INT PRIMARY KEY,
    Data DATE,
    Dia INT,
    Mes INT,
    Ano INT,
    Trimestre INT,
    Semestre INT
);

CREATE TABLE FatoProfessor (
    ProfessorID INT,
    CursoID INT,
    DepartamentoID INT,
    DataID INT,
    HorasMinistradas INT,
    NumeroAlunos INT,
    PRIMARY KEY (ProfessorID, CursoID, DepartamentoID, DataID),
    FOREIGN KEY (ProfessorID) REFERENCES DimensaoProfessor(ProfessorID),
    FOREIGN KEY (CursoID) REFERENCES DimensaoCurso(CursoID),
    FOREIGN KEY (DepartamentoID) REFERENCES DimensaoDepartamento(DepartamentoID),
    FOREIGN KEY (DataID) REFERENCES DimensaoData(DataID)
);

DateTable = CALENDAR(MIN(FatoProfessor[DataInicio]), MAX(FatoProfessor[DataFim]))

TotalHorasMinistradas = SUM(FatoProfessor[HorasMinistradas])
NumeroAlunos = SUM(FatoProfessor[NumeroAlunos])```





















