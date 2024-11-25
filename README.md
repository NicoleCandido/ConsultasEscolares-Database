# ConsultasEscolares-Database
consultas_escolares.sql

CREATE SCHEMA IF NOT EXISTS ConsultasEscolares DEFAULT CHARACTER SET utf8;
use ConsultasEscolares;

	CREATE TABLE IF NOT EXISTS Aluno (
    id integer not null,
    nome VARCHAR(255) ,
    email VARCHAR(255) ,
	DataNascimento datetime,
    primary key (id)
    ) ENGINE = InnoDB;
    
    select * from Aluno;
    
    CREATE TABLE IF NOT EXISTS Turma (
    id integer not null,
    inicio datetime,
    fim datetime,
	observações longtext,
    primary key (id)
    ) ENGINE = InnoDB;
    drop table Aluno;
    
    select * from Turma;
    
    CREATE TABLE IF NOT EXISTS AlunoTurma (
    Aluno_id integer not null,
    Turma_id integer not null,
    primary key (Aluno_id, Turma_id),
    foreign key (Aluno_id) references Aluno(id),
    foreign key (Turma_id) references Turma(id)
    ) ENGINE = InnoDB;
    
    select * from AlunoTurma;
    
        INSERT INTO Aluno VALUES (6,'Felicia Tomaz', 'felicia@gmail.com','2001-08-20');
        INSERT INTO Aluno VALUES (5,'Lais Marciel', 'luisalgusto@gmail.com','2002-04-03');
        INSERT INTO Aluno VALUES (4,'Sarah Gomes', 'Gomes@gmail.com','2001-09-12');
		INSERT INTO Aluno VALUES (3,'Douglas Franco', 'franco@gmail.com','2001-02-28');
        INSERT INTO Aluno VALUES (2,'Lucas Marques', 'lucasmarques@gmail.com','2001-11-19');
        INSERT INTO Aluno VALUES (1,'Clara Reis', 'clara@gmail.com','2002-06-23');
        
		INSERT INTO Turma VALUES (1,'2019-03-01','2019-07-15', 'turma banco de dados I');
        INSERT INTO Turma VALUES (2,'2019-03-01','2019-07-15', 'turma banco de dados II');
        
        INSERT INTO AlunoTurma VALUES (1,1);
        INSERT INTO AlunoTurma VALUES (2,1);
        INSERT INTO AlunoTurma VALUES (3,2);
        
CREATE TABLE IF NOT EXISTS Nota (
    id int not null,
    Aluno_id integer not null,
    Turma_id integer not null,
    nota decimal,
    primary key (id),
    foreign key (Aluno_id) references Aluno(id),
    foreign key (Turma_id) references Turma(id)
    ) ENGINE = InnoDB;
    
    select * from Nota;
    
    INSERT INTO Nota VALUES (1,1,1,10);
    INSERT INTO Nota VALUES (2,2,2,8);
    INSERT INTO Nota VALUES (3,3,1,5);
    INSERT INTO Nota VALUES (4,4,2,10);
    INSERT INTO Nota VALUES (5,4,1,4);
    
    select * from Nota as n1
    where n1.Nota >(
    select avg (n2.Nota)
    from Nota as n2
    where n2.Turma_id = n1.Turma_id);

     select n1.*, (
    select max(n2.Nota)
    from Nota as n2
    where n2.Turma_id = 1)
    as maior_Nota from Nota as n1
    where n1.Turma_id;
    
     select n1.*, (
    select max(n2.Nota)
    from Nota as n2
    where n2.Turma_id = 1)
    as maior_Nota from Nota as n1
    where n1.Turma_id or n1.Turma_id= 2;
