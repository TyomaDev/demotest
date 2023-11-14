Структура:

--------
 Матчи
--------
| PK ID_Матча int not null |  
| FK ID_Команды_1 int not null |   
| FK ID_Команды_1 int not null |  
| Дата date not null |  
| Результат nvarchar(MAX) |  
| Описание nvarchar(MAX) |  
| Место_проведения  nvarchar(MAX) |  
-------------------------------

----------
 Команда
----------
| PK ID_Команды int not null |  
| Название nvarchar(MAX) |  
| FK ID_Тренера int not null |  
--------------------------

-------------
 Футболисты
-------------
| PK id int not null |  
| ФИО nvarchar(MAX) not null |  
| Роль nvarchar(MAX) not null |  
| Возраст int not null |  
--------------------------

---------
 Тренер
---------
| PK ID_Тренера int not null |  
| Фамилия nvarchar(MAX) not null |  
| Имя nvarchar(MAX) not null |  
| Отчество nvarchar(MAX) |  
| Биография nvarchar(MAX) |  
| Категория nvarchar(MAX) |  
| Награды nvarchar(MAX) |  
--------------------------


_________________________________________________________________________________________
_________________________________________________________________________________________

SQL-запрос:

USE [master]
GO
/****** Object:  Database [Football]    Script Date: 14.11.2023 10:39:03 ******/
CREATE DATABASE [Football]
 CONTAINMENT = NONE
 ON  PRIMARY 
( NAME = N'Football', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL15.SQLEXPRESS\MSSQL\DATA\Football.mdf' , SIZE = 8192KB , MAXSIZE = UNLIMITED, FILEGROWTH = 65536KB )
 LOG ON 
( NAME = N'Football_log', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL15.SQLEXPRESS\MSSQL\DATA\Football_log.ldf' , SIZE = 8192KB , MAXSIZE = 2048GB , FILEGROWTH = 65536KB )
 WITH CATALOG_COLLATION = DATABASE_DEFAULT
GO
ALTER DATABASE [Football] SET COMPATIBILITY_LEVEL = 150
GO
IF (1 = FULLTEXTSERVICEPROPERTY('IsFullTextInstalled'))
begin
EXEC [Football].[dbo].[sp_fulltext_database] @action = 'enable'
end
GO
ALTER DATABASE [Football] SET ANSI_NULL_DEFAULT OFF 
GO
ALTER DATABASE [Football] SET ANSI_NULLS OFF 
GO
ALTER DATABASE [Football] SET ANSI_PADDING OFF 
GO
ALTER DATABASE [Football] SET ANSI_WARNINGS OFF 
GO
ALTER DATABASE [Football] SET ARITHABORT OFF 
GO
ALTER DATABASE [Football] SET AUTO_CLOSE OFF 
GO
ALTER DATABASE [Football] SET AUTO_SHRINK OFF 
GO
ALTER DATABASE [Football] SET AUTO_UPDATE_STATISTICS ON 
GO
ALTER DATABASE [Football] SET CURSOR_CLOSE_ON_COMMIT OFF 
GO
ALTER DATABASE [Football] SET CURSOR_DEFAULT  GLOBAL 
GO
ALTER DATABASE [Football] SET CONCAT_NULL_YIELDS_NULL OFF 
GO
ALTER DATABASE [Football] SET NUMERIC_ROUNDABORT OFF 
GO
ALTER DATABASE [Football] SET QUOTED_IDENTIFIER OFF 
GO
ALTER DATABASE [Football] SET RECURSIVE_TRIGGERS OFF 
GO
ALTER DATABASE [Football] SET  DISABLE_BROKER 
GO
ALTER DATABASE [Football] SET AUTO_UPDATE_STATISTICS_ASYNC OFF 
GO
ALTER DATABASE [Football] SET DATE_CORRELATION_OPTIMIZATION OFF 
GO
ALTER DATABASE [Football] SET TRUSTWORTHY OFF 
GO
ALTER DATABASE [Football] SET ALLOW_SNAPSHOT_ISOLATION OFF 
GO
ALTER DATABASE [Football] SET PARAMETERIZATION SIMPLE 
GO
ALTER DATABASE [Football] SET READ_COMMITTED_SNAPSHOT OFF 
GO
ALTER DATABASE [Football] SET HONOR_BROKER_PRIORITY OFF 
GO
ALTER DATABASE [Football] SET RECOVERY SIMPLE 
GO
ALTER DATABASE [Football] SET  MULTI_USER 
GO
ALTER DATABASE [Football] SET PAGE_VERIFY CHECKSUM  
GO
ALTER DATABASE [Football] SET DB_CHAINING OFF 
GO
ALTER DATABASE [Football] SET FILESTREAM( NON_TRANSACTED_ACCESS = OFF ) 
GO
ALTER DATABASE [Football] SET TARGET_RECOVERY_TIME = 60 SECONDS 
GO
ALTER DATABASE [Football] SET DELAYED_DURABILITY = DISABLED 
GO
ALTER DATABASE [Football] SET ACCELERATED_DATABASE_RECOVERY = OFF  
GO
ALTER DATABASE [Football] SET QUERY_STORE = OFF
GO
USE [Football]
GO
/****** Object:  Table [dbo].[Команда]    Script Date: 14.11.2023 10:39:04 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Команда](
	[ID_команды] [int] IDENTITY(1,1) NOT NULL,
	[Название] [nvarchar](max) NULL,
	[ID_тренера] [int] NOT NULL,
 CONSTRAINT [PK__Команда__2C7480B4F8A977C6] PRIMARY KEY CLUSTERED 
(
	[ID_команды] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Матчи]    Script Date: 14.11.2023 10:39:04 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Матчи](
	[ID_матча] [int] IDENTITY(1,1) NOT NULL,
	[ID_команды_1] [int] NULL,
	[ID_команды_2] [int] NULL,
	[Дата] [date] NULL,
	[Результат] [nvarchar](max) NULL,
	[Описание] [nvarchar](max) NULL,
	[Место_проведения] [nvarchar](max) NULL,
 CONSTRAINT [PK__Матчи__058116F57AFA0ABD] PRIMARY KEY CLUSTERED 
(
	[ID_матча] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Тренер]    Script Date: 14.11.2023 10:39:04 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Тренер](
	[ID_тренера] [int] IDENTITY(1,1) NOT NULL,
	[Фамилия] [nvarchar](max) NOT NULL,
	[Имя] [nvarchar](max) NOT NULL,
	[Отчество] [nvarchar](max) NOT NULL,
	[Биография] [nvarchar](max) NULL,
	[Категория] [nvarchar](max) NULL,
	[Награды] [nvarchar](max) NULL,
 CONSTRAINT [PK__Тренер__751725289C451788] PRIMARY KEY CLUSTERED 
(
	[ID_тренера] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Футболисты]    Script Date: 14.11.2023 10:39:04 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Футболисты](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[ФИО] [nvarchar](150) NULL,
	[id_команды] [int] NULL,
	[Роль] [nvarchar](150) NULL,
	[Возраст] [int] NULL,
 CONSTRAINT [PK_Футболисты] PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
ALTER TABLE [dbo].[Команда]  WITH CHECK ADD  CONSTRAINT [FK__Команда__ID_трен__398D8EEE] FOREIGN KEY([ID_тренера])
REFERENCES [dbo].[Тренер] ([ID_тренера])
GO
ALTER TABLE [dbo].[Команда] CHECK CONSTRAINT [FK__Команда__ID_трен__398D8EEE]
GO
ALTER TABLE [dbo].[Матчи]  WITH CHECK ADD  CONSTRAINT [FK__Матчи__ID_команд__3C69FB99] FOREIGN KEY([ID_команды_1])
REFERENCES [dbo].[Команда] ([ID_команды])
GO
ALTER TABLE [dbo].[Матчи] CHECK CONSTRAINT [FK__Матчи__ID_команд__3C69FB99]
GO
ALTER TABLE [dbo].[Матчи]  WITH CHECK ADD  CONSTRAINT [FK__Матчи__ID_команд__3D5E1FD2] FOREIGN KEY([ID_команды_2])
REFERENCES [dbo].[Команда] ([ID_команды])
GO
ALTER TABLE [dbo].[Матчи] CHECK CONSTRAINT [FK__Матчи__ID_команд__3D5E1FD2]
GO
ALTER TABLE [dbo].[Футболисты]  WITH CHECK ADD  CONSTRAINT [FK_Футболисты_Команда] FOREIGN KEY([id_команды])
REFERENCES [dbo].[Команда] ([ID_команды])
GO
ALTER TABLE [dbo].[Футболисты] CHECK CONSTRAINT [FK_Футболисты_Команда]
GO
USE [master]
GO
ALTER DATABASE [Football] SET  READ_WRITE 
GO
