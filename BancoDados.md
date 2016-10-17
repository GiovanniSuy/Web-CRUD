
USE [master]
GO
/****** Object:  Database [CRUDG]    Script Date: 17/10/2016 15:38:38 ******/
CREATE DATABASE [CRUDG]
 CONTAINMENT = NONE
 ON  PRIMARY 
( NAME = N'CRUDG', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.SQLEXPRESS\MSSQL\DATA\CRUDG.mdf' , SIZE = 5120KB , MAXSIZE = UNLIMITED, FILEGROWTH = 1024KB )
 LOG ON 
( NAME = N'CRUDG_log', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.SQLEXPRESS\MSSQL\DATA\CRUDG_log.ldf' , SIZE = 2048KB , MAXSIZE = 2048GB , FILEGROWTH = 10%)
GO
ALTER DATABASE [CRUDG] SET COMPATIBILITY_LEVEL = 120
GO
IF (1 = FULLTEXTSERVICEPROPERTY('IsFullTextInstalled'))
begin
EXEC [CRUDG].[dbo].[sp_fulltext_database] @action = 'enable'
end
GO
ALTER DATABASE [CRUDG] SET ANSI_NULL_DEFAULT OFF 
GO
ALTER DATABASE [CRUDG] SET ANSI_NULLS OFF 
GO
ALTER DATABASE [CRUDG] SET ANSI_PADDING OFF 
GO
ALTER DATABASE [CRUDG] SET ANSI_WARNINGS OFF 
GO
ALTER DATABASE [CRUDG] SET ARITHABORT OFF 
GO
ALTER DATABASE [CRUDG] SET AUTO_CLOSE OFF 
GO
ALTER DATABASE [CRUDG] SET AUTO_SHRINK OFF 
GO
ALTER DATABASE [CRUDG] SET AUTO_UPDATE_STATISTICS ON 
GO
ALTER DATABASE [CRUDG] SET CURSOR_CLOSE_ON_COMMIT OFF 
GO
ALTER DATABASE [CRUDG] SET CURSOR_DEFAULT  GLOBAL 
GO
ALTER DATABASE [CRUDG] SET CONCAT_NULL_YIELDS_NULL OFF 
GO
ALTER DATABASE [CRUDG] SET NUMERIC_ROUNDABORT OFF 
GO
ALTER DATABASE [CRUDG] SET QUOTED_IDENTIFIER OFF 
GO
ALTER DATABASE [CRUDG] SET RECURSIVE_TRIGGERS OFF 
GO
ALTER DATABASE [CRUDG] SET  DISABLE_BROKER 
GO
ALTER DATABASE [CRUDG] SET AUTO_UPDATE_STATISTICS_ASYNC OFF 
GO
ALTER DATABASE [CRUDG] SET DATE_CORRELATION_OPTIMIZATION OFF 
GO
ALTER DATABASE [CRUDG] SET TRUSTWORTHY OFF 
GO
ALTER DATABASE [CRUDG] SET ALLOW_SNAPSHOT_ISOLATION OFF 
GO
ALTER DATABASE [CRUDG] SET PARAMETERIZATION SIMPLE 
GO
ALTER DATABASE [CRUDG] SET READ_COMMITTED_SNAPSHOT OFF 
GO
ALTER DATABASE [CRUDG] SET HONOR_BROKER_PRIORITY OFF 
GO
ALTER DATABASE [CRUDG] SET RECOVERY SIMPLE 
GO
ALTER DATABASE [CRUDG] SET  MULTI_USER 
GO
ALTER DATABASE [CRUDG] SET PAGE_VERIFY CHECKSUM  
GO
ALTER DATABASE [CRUDG] SET DB_CHAINING OFF 
GO
ALTER DATABASE [CRUDG] SET FILESTREAM( NON_TRANSACTED_ACCESS = OFF ) 
GO
ALTER DATABASE [CRUDG] SET TARGET_RECOVERY_TIME = 0 SECONDS 
GO
ALTER DATABASE [CRUDG] SET DELAYED_DURABILITY = DISABLED 
GO
USE [CRUDG]
GO
/****** Object:  Table [dbo].[Empresa]    Script Date: 17/10/2016 15:38:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Empresa](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Nome] [nvarchar](30) NOT NULL,
	[Responsavel] [nvarchar](20) NOT NULL,
	[Email] [nvarchar](40) NOT NULL,
 CONSTRAINT [PK_Empresa] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]

GO
/****** Object:  Table [dbo].[Ordem]    Script Date: 17/10/2016 15:38:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Ordem](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Nome] [nvarchar](max) NOT NULL,
	[Prazo] [date] NOT NULL,
	[Comissao] [int] NOT NULL,
	[Id_Empresa] [int] NOT NULL,
	[Id_Pessoa] [int] NOT NULL,
 CONSTRAINT [PK_Ordem] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]

GO
/****** Object:  Table [dbo].[Pessoa]    Script Date: 17/10/2016 15:38:38 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Pessoa](
	[Id] [int] IDENTITY(1,1) NOT NULL,
	[Nome] [nvarchar](30) NOT NULL,
	[Endereco] [nvarchar](60) NOT NULL,
	[Email] [nvarchar](40) NOT NULL,
 CONSTRAINT [PK_Pessoa] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]

GO
SET IDENTITY_INSERT [dbo].[Empresa] ON 

INSERT [dbo].[Empresa] ([Id], [Nome], [Responsavel], [Email]) VALUES (1, N'Microsoft', N'Satya Nadella', N'sat@hotmail.com')
INSERT [dbo].[Empresa] ([Id], [Nome], [Responsavel], [Email]) VALUES (2, N'Google ltc', N'alan', N'alan@google.com')
INSERT [dbo].[Empresa] ([Id], [Nome], [Responsavel], [Email]) VALUES (3, N'TOTVS', N'Guilherme', N'guilherme@gmail.com')
SET IDENTITY_INSERT [dbo].[Empresa] OFF
SET IDENTITY_INSERT [dbo].[Ordem] ON 

INSERT [dbo].[Ordem] ([Id], [Nome], [Prazo], [Comissao], [Id_Empresa], [Id_Pessoa]) VALUES (1, N'Formatar maquina 12', CAST(N'2016-10-20' AS Date), 100, 1, 2)
INSERT [dbo].[Ordem] ([Id], [Nome], [Prazo], [Comissao], [Id_Empresa], [Id_Pessoa]) VALUES (2, N'Arrumar rede da sala 13', CAST(N'2016-10-22' AS Date), 150, 1, 4)
INSERT [dbo].[Ordem] ([Id], [Nome], [Prazo], [Comissao], [Id_Empresa], [Id_Pessoa]) VALUES (3, N'fomatar maquinha 202 do salao 3', CAST(N'2016-10-22' AS Date), 200, 2, 4)
INSERT [dbo].[Ordem] ([Id], [Nome], [Prazo], [Comissao], [Id_Empresa], [Id_Pessoa]) VALUES (5, N'web site com orientado a serviço', CAST(N'2017-02-01' AS Date), 2000, 3, 6)
SET IDENTITY_INSERT [dbo].[Ordem] OFF
SET IDENTITY_INSERT [dbo].[Pessoa] ON 

INSERT [dbo].[Pessoa] ([Id], [Nome], [Endereco], [Email]) VALUES (2, N'Joao Moscao doido', N'rua menda gasalao', N'jao23@gmail.com')
INSERT [dbo].[Pessoa] ([Id], [Nome], [Endereco], [Email]) VALUES (3, N'Fulano doido', N'rua dos fulanos', N'fulano@gmail.com')
INSERT [dbo].[Pessoa] ([Id], [Nome], [Endereco], [Email]) VALUES (4, N'Bruno alafuca', N'rua dos 12 centavos', N'falafuca@valido.com')
INSERT [dbo].[Pessoa] ([Id], [Nome], [Endereco], [Email]) VALUES (5, N'Daniel viadao', N'rua dos batma', N'danel___@gmail.com')
INSERT [dbo].[Pessoa] ([Id], [Nome], [Endereco], [Email]) VALUES (6, N'Giovanni', N'Rua sem suico corioco', N'giovanni@yahoo.com')
SET IDENTITY_INSERT [dbo].[Pessoa] OFF
ALTER TABLE [dbo].[Ordem]  WITH CHECK ADD  CONSTRAINT [FK_Ordem_Empresa] FOREIGN KEY([Id_Empresa])
REFERENCES [dbo].[Empresa] ([Id])
GO
ALTER TABLE [dbo].[Ordem] CHECK CONSTRAINT [FK_Ordem_Empresa]
GO
ALTER TABLE [dbo].[Ordem]  WITH CHECK ADD  CONSTRAINT [FK_Ordem_Pessoa] FOREIGN KEY([Id_Pessoa])
REFERENCES [dbo].[Pessoa] ([Id])
GO
ALTER TABLE [dbo].[Ordem] CHECK CONSTRAINT [FK_Ordem_Pessoa]
GO
USE [master]
GO
ALTER DATABASE [CRUDG] SET  READ_WRITE 
GO
