
/****** Object:  Database [ITForumDB]    Script Date: 27.02.2026 2:06:37 ******/
CREATE DATABASE [ITForumDB]
GO
USE [ITForumDB]
GO
/****** Object:  Table [dbo].[Articles]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Articles](
	[ArticleID] [int] IDENTITY(1,1) NOT NULL,
	[Title] [nvarchar](100) NOT NULL,
	[Summary] [nvarchar](100) NULL,
	[Content] [nvarchar](max) NOT NULL,
	[Date] [date] NOT NULL,
	[StatusID] [int] NOT NULL,
	[AuthorID] [int] NOT NULL,
	[PartnerID] [int] NULL,
 CONSTRAINT [PK__Articles__9C6270C86269524B] PRIMARY KEY CLUSTERED 
(
	[ArticleID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[ArticleStatuses]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[ArticleStatuses](
	[StatusID] [int] IDENTITY(1,1) NOT NULL,
	[Status] [nvarchar](50) NOT NULL,
 CONSTRAINT [PK_ArticleStatuses] PRIMARY KEY CLUSTERED 
(
	[StatusID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Comments]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Comments](
	[CommentID] [int] IDENTITY(1,1) NOT NULL,
	[ArticleID] [int] NOT NULL,
	[UserID] [int] NOT NULL,
	[Content] [nvarchar](500) NOT NULL,
	[Date] [date] NOT NULL,
	[IsDeleted] [bit] NOT NULL,
 CONSTRAINT [PK__Comments__C3B4DFAA074476C1] PRIMARY KEY CLUSTERED 
(
	[CommentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Partners]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Partners](
	[PartnerID] [int] IDENTITY(1,1) NOT NULL,
	[PartnerName] [nvarchar](50) NOT NULL,
	[ContactInfo] [nvarchar](100) NOT NULL,
 CONSTRAINT [PK__Partners__39FD6332986572DF] PRIMARY KEY CLUSTERED 
(
	[PartnerID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Roles]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Roles](
	[RoleID] [int] IDENTITY(1,1) NOT NULL,
	[RoleName] [nvarchar](30) NOT NULL,
 CONSTRAINT [PK__Roles__8AFACE3AABA7967A] PRIMARY KEY CLUSTERED 
(
	[RoleID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[UserRoles]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[UserRoles](
	[UserID] [int] NOT NULL,
	[RoleID] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[UserID] ASC,
	[RoleID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Users]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Users](
	[UserID] [int] IDENTITY(1,1) NOT NULL,
	[Login] [nvarchar](20) NOT NULL,
	[Password] [nvarchar](20) NOT NULL,
	[Username] [nvarchar](20) NOT NULL,
	[Email] [nvarchar](30) NULL,
	[CreationDate] [date] NOT NULL,
 CONSTRAINT [PK__Users__1788CCAC214CF7C3] PRIMARY KEY CLUSTERED 
(
	[UserID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
SET IDENTITY_INSERT [dbo].[Articles] ON 

INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (1, N'Тренды искусственного интеллекта', N'Обзор современных ИИ', N'Подробная статья о развитии искусственного интеллекта', CAST(N'2024-02-01' AS Date), 1, 2, 1)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (2, N'Основы облачных технологий', N'Введение в облака', N'Статья о принципах работы облачных сервисов', CAST(N'2024-02-02' AS Date), 1, 3, NULL)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (3, N'Безопасность веб-приложений', N'Советы по защите', N'Материал о защите сайтов и сервисов', CAST(N'2024-02-03' AS Date), 1, 7, NULL)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (4, N'Руководство по DevOps', N'CI/CD и автоматизация', N'Подробный гайд по DevOps-практикам', CAST(N'2024-02-04' AS Date), 2, 10, 4)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (5, N'Большие данные', N'Анализ и обработка', N'Статья о технологиях Big Data', CAST(N'2024-02-05' AS Date), 3, 2, NULL)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (6, N'Мобильная разработка', N'Приложения под Android и iOS', N'Материал о создании мобильных приложений', CAST(N'2024-02-06' AS Date), 1, 3, NULL)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (7, N'UX-дизайн', N'Основы пользовательского опыта', N'Статья о проектировании интерфейсов', CAST(N'2024-02-07' AS Date), 2, 7, 2)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (8, N'Базы данных', N'SQL и NoSQL', N'Обзор современных СУБД', CAST(N'2024-02-08' AS Date), 1, 10, NULL)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (9, N'Компьютерные сети', N'Протоколы и архитектура', N'Материал о сетевых технологиях', CAST(N'2024-02-09' AS Date), 2, 2, 4)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (10, N'Разработка игр', N'Введение в геймдев', N'Статья о создании игр', CAST(N'2024-02-10' AS Date), 1, 3, 5)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (11, N'Тестирование ПО', N'Основы QA', N'Материал о тестировании программ', CAST(N'2024-02-11' AS Date), 1, 7, 6)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (12, N'Администрирование Linux', N'Практическое руководство', N'Статья по управлению Linux-серверами', CAST(N'2024-02-12' AS Date), 2, 10, NULL)
SET IDENTITY_INSERT [dbo].[Articles] OFF
GO
SET IDENTITY_INSERT [dbo].[ArticleStatuses] ON 

INSERT [dbo].[ArticleStatuses] ([StatusID], [Status]) VALUES (1, N'Опубликована')
INSERT [dbo].[ArticleStatuses] ([StatusID], [Status]) VALUES (2, N'На проверке')
INSERT [dbo].[ArticleStatuses] ([StatusID], [Status]) VALUES (3, N'Отклонена')
SET IDENTITY_INSERT [dbo].[ArticleStatuses] OFF
GO
SET IDENTITY_INSERT [dbo].[Comments] ON 

INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (1, 1, 4, N'Отличная статья!', CAST(N'2024-02-01' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (2, 1, 5, N'Очень полезно', CAST(N'2024-02-01' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (3, 2, 6, N'Спасибо за материал', CAST(N'2024-02-02' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (4, 2, 7, N'Хорошо объяснено', CAST(N'2024-02-02' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (5, 3, 8, N'Не хватает примеров', CAST(N'2024-02-03' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (6, 3, 9, N'Актуальная тема', CAST(N'2024-02-03' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (7, 4, 10, N'Полезная информация', CAST(N'2024-02-04' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (8, 4, 4, N'Отлично написано', CAST(N'2024-02-04' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (9, 5, 5, N'Неинтересно', CAST(N'2024-02-05' AS Date), 1)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (10, 6, 6, N'Очень интересно', CAST(N'2024-02-06' AS Date), 1)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (11, 6, 7, N'Узнал много нового', CAST(N'2024-02-06' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (12, 7, 8, N'Статья короткая', CAST(N'2024-02-07' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (13, 8, 9, N'Отличный обзор', CAST(N'2024-02-08' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (14, 8, 4, N'Всё понятно и доступно', CAST(N'2024-02-08' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (15, 9, 5, N'Автор глупый', CAST(N'2024-02-09' AS Date), 1)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (16, 10, 6, N'Классная статья', CAST(N'2024-02-10' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (17, 10, 7, N'Понравилось', CAST(N'2024-02-10' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (18, 11, 8, N'Жду продолжения', CAST(N'2024-02-11' AS Date), 1)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (19, 12, 9, N'Писатель криворукий', CAST(N'2024-02-12' AS Date), 1)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (20, 12, 10, N'Спасибо автору', CAST(N'2024-02-12' AS Date), 0)
SET IDENTITY_INSERT [dbo].[Comments] OFF
GO
SET IDENTITY_INSERT [dbo].[Partners] ON 

INSERT [dbo].[Partners] ([PartnerID], [PartnerName], [ContactInfo]) VALUES (1, N'OpenAI', N'contact@openai.com')
INSERT [dbo].[Partners] ([PartnerID], [PartnerName], [ContactInfo]) VALUES (2, N'МАХ', N'info@yandex.com')
INSERT [dbo].[Partners] ([PartnerID], [PartnerName], [ContactInfo]) VALUES (3, N'Google', N'support@google.com')
INSERT [dbo].[Partners] ([PartnerID], [PartnerName], [ContactInfo]) VALUES (4, N'АО3', N'aws@amo.com')
INSERT [dbo].[Partners] ([PartnerID], [PartnerName], [ContactInfo]) VALUES (5, N'Meta', N'meta@meta.com')
INSERT [dbo].[Partners] ([PartnerID], [PartnerName], [ContactInfo]) VALUES (6, N'Яндекс', N'info@yandex.ru')
SET IDENTITY_INSERT [dbo].[Partners] OFF
GO
SET IDENTITY_INSERT [dbo].[Roles] ON 

INSERT [dbo].[Roles] ([RoleID], [RoleName]) VALUES (4, N'Автор')
INSERT [dbo].[Roles] ([RoleID], [RoleName]) VALUES (1, N'Администратор')
INSERT [dbo].[Roles] ([RoleID], [RoleName]) VALUES (2, N'Модератор')
INSERT [dbo].[Roles] ([RoleID], [RoleName]) VALUES (5, N'Пользователь')
INSERT [dbo].[Roles] ([RoleID], [RoleName]) VALUES (3, N'Редактор')
SET IDENTITY_INSERT [dbo].[Roles] OFF
GO
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (1, 1)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (1, 4)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (2, 2)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (3, 5)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (4, 3)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (5, 5)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (6, 3)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (7, 2)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (8, 3)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (9, 4)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (10, 2)
GO
SET IDENTITY_INSERT [dbo].[Users] ON 

INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (1, N'admin', N'admin123', N'Администратор', N'admin@mail.com', CAST(N'2024-01-01' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (2, N'ivanov', N'pass123', N'Иван Иванов', N'ivan@mail.com', CAST(N'2024-01-05' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (3, N'petrov', N'qwerty', N'Пётр Петров', N'petr@mail.com', CAST(N'2024-01-06' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (4, N'anna', N'anna123', N'Анна Смирнова', N'anna@mail.com', CAST(N'2024-01-07' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (5, N'sergey', N'serg123', N'Сергей Кузнецов', N'serg@mail.com', CAST(N'2024-01-08' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (6, N'olga', N'olga123', N'Ольга Иванова', N'olga@mail.com', CAST(N'2024-01-09' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (7, N'max', N'max123', N'Максим Волков', N'max@mail.com', CAST(N'2024-01-10' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (8, N'kate', N'kate123', N'Екатерина Орлова', N'kate@mail.com', CAST(N'2024-01-11' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (9, N'dima', N'dima123', N'Дмитрий Соколов', N'dima@mail.com', CAST(N'2024-01-12' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (10, N'alex', N'alex123', N'Алексей Морозов', N'alex@mail.com', CAST(N'2024-01-13' AS Date))
SET IDENTITY_INSERT [dbo].[Users] OFF
GO
SET ANSI_PADDING ON
GO
/****** Object:  Index [UQ__Roles__737584F6FD9E052B]    Script Date: 27.02.2026 2:06:38 ******/
ALTER TABLE [dbo].[Roles] ADD  CONSTRAINT [UQ__Roles__737584F6FD9E052B] UNIQUE NONCLUSTERED 
(
	[RoleName] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, SORT_IN_TEMPDB = OFF, IGNORE_DUP_KEY = OFF, ONLINE = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
GO
SET ANSI_PADDING ON
GO
/****** Object:  Index [UQ__Users__5E55825BD2844DFA]    Script Date: 27.02.2026 2:06:38 ******/
ALTER TABLE [dbo].[Users] ADD  CONSTRAINT [UQ__Users__5E55825BD2844DFA] UNIQUE NONCLUSTERED 
(
	[Login] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, SORT_IN_TEMPDB = OFF, IGNORE_DUP_KEY = OFF, ONLINE = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
GO
ALTER TABLE [dbo].[Comments] ADD  CONSTRAINT [DF__Comments__Create__5AEE82B9]  DEFAULT (getdate()) FOR [Date]
GO
ALTER TABLE [dbo].[Comments] ADD  CONSTRAINT [DF__Comments__IsDele__5BE2A6F2]  DEFAULT ((0)) FOR [IsDeleted]
GO
ALTER TABLE [dbo].[Articles]  WITH CHECK ADD  CONSTRAINT [FK_Articles_ArticleStatuses] FOREIGN KEY([StatusID])
REFERENCES [dbo].[ArticleStatuses] ([StatusID])
GO
ALTER TABLE [dbo].[Articles] CHECK CONSTRAINT [FK_Articles_ArticleStatuses]
GO
ALTER TABLE [dbo].[Articles]  WITH CHECK ADD  CONSTRAINT [FK_Articles_Partners] FOREIGN KEY([PartnerID])
REFERENCES [dbo].[Partners] ([PartnerID])
GO
ALTER TABLE [dbo].[Articles] CHECK CONSTRAINT [FK_Articles_Partners]
GO
ALTER TABLE [dbo].[Comments]  WITH CHECK ADD  CONSTRAINT [FK_Comments_Articles] FOREIGN KEY([ArticleID])
REFERENCES [dbo].[Articles] ([ArticleID])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[Comments] CHECK CONSTRAINT [FK_Comments_Articles]
GO
ALTER TABLE [dbo].[Comments]  WITH CHECK ADD  CONSTRAINT [FK_Comments_Users] FOREIGN KEY([UserID])
REFERENCES [dbo].[Users] ([UserID])
GO
ALTER TABLE [dbo].[Comments] CHECK CONSTRAINT [FK_Comments_Users]
GO
ALTER TABLE [dbo].[UserRoles]  WITH CHECK ADD  CONSTRAINT [FK_UserRoles_Roles] FOREIGN KEY([RoleID])
REFERENCES [dbo].[Roles] ([RoleID])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[UserRoles] CHECK CONSTRAINT [FK_UserRoles_Roles]
GO
ALTER TABLE [dbo].[UserRoles]  WITH CHECK ADD  CONSTRAINT [FK_UserRoles_Users] FOREIGN KEY([UserID])
REFERENCES [dbo].[Users] ([UserID])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[UserRoles] CHECK CONSTRAINT [FK_UserRoles_Users]
GO
USE [master]
GO
ALTER DATABASE [ITForumDB] SET  READ_WRITE 
GO

=========================================
USE [master]
GO
/****** Object:  Database [ITForumDB]    Script Date: 27.02.2026 2:06:37 ******/
CREATE DATABASE [ITForumDB]
GO
USE [ITForumDB]
GO
/****** Object:  Table [dbo].[Articles]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Articles](
	[ArticleID] [int] IDENTITY(1,1) NOT NULL,
	[Title] [nvarchar](100) NOT NULL,
	[Summary] [nvarchar](100) NULL,
	[Content] [nvarchar](max) NOT NULL,
	[Date] [date] NOT NULL,
	[StatusID] [int] NOT NULL,
	[AuthorID] [int] NOT NULL,
	[PartnerID] [int] NULL,
 CONSTRAINT [PK__Articles__9C6270C86269524B] PRIMARY KEY CLUSTERED 
(
	[ArticleID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[ArticleStatuses]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[ArticleStatuses](
	[StatusID] [int] IDENTITY(1,1) NOT NULL,
	[Status] [nvarchar](50) NOT NULL,
 CONSTRAINT [PK_ArticleStatuses] PRIMARY KEY CLUSTERED 
(
	[StatusID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Comments]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Comments](
	[CommentID] [int] IDENTITY(1,1) NOT NULL,
	[ArticleID] [int] NOT NULL,
	[UserID] [int] NOT NULL,
	[Content] [nvarchar](500) NOT NULL,
	[Date] [date] NOT NULL,
	[IsDeleted] [bit] NOT NULL,
 CONSTRAINT [PK__Comments__C3B4DFAA074476C1] PRIMARY KEY CLUSTERED 
(
	[CommentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Partners]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Partners](
	[PartnerID] [int] IDENTITY(1,1) NOT NULL,
	[PartnerName] [nvarchar](50) NOT NULL,
	[ContactInfo] [nvarchar](100) NOT NULL,
 CONSTRAINT [PK__Partners__39FD6332986572DF] PRIMARY KEY CLUSTERED 
(
	[PartnerID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Roles]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Roles](
	[RoleID] [int] IDENTITY(1,1) NOT NULL,
	[RoleName] [nvarchar](30) NOT NULL,
 CONSTRAINT [PK__Roles__8AFACE3AABA7967A] PRIMARY KEY CLUSTERED 
(
	[RoleID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[UserRoles]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[UserRoles](
	[UserID] [int] NOT NULL,
	[RoleID] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[UserID] ASC,
	[RoleID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Users]    Script Date: 27.02.2026 2:06:37 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Users](
	[UserID] [int] IDENTITY(1,1) NOT NULL,
	[Login] [nvarchar](20) NOT NULL,
	[Password] [nvarchar](20) NOT NULL,
	[Username] [nvarchar](20) NOT NULL,
	[Email] [nvarchar](30) NULL,
	[CreationDate] [date] NOT NULL,
 CONSTRAINT [PK__Users__1788CCAC214CF7C3] PRIMARY KEY CLUSTERED 
(
	[UserID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
SET IDENTITY_INSERT [dbo].[Articles] ON 

INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (1, N'Тренды искусственного интеллекта', N'Обзор современных ИИ', N'Подробная статья о развитии искусственного интеллекта', CAST(N'2024-02-01' AS Date), 1, 2, 1)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (2, N'Основы облачных технологий', N'Введение в облака', N'Статья о принципах работы облачных сервисов', CAST(N'2024-02-02' AS Date), 1, 3, NULL)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (3, N'Безопасность веб-приложений', N'Советы по защите', N'Материал о защите сайтов и сервисов', CAST(N'2024-02-03' AS Date), 1, 7, NULL)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (4, N'Руководство по DevOps', N'CI/CD и автоматизация', N'Подробный гайд по DevOps-практикам', CAST(N'2024-02-04' AS Date), 2, 10, 4)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (5, N'Большие данные', N'Анализ и обработка', N'Статья о технологиях Big Data', CAST(N'2024-02-05' AS Date), 3, 2, NULL)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (6, N'Мобильная разработка', N'Приложения под Android и iOS', N'Материал о создании мобильных приложений', CAST(N'2024-02-06' AS Date), 1, 3, NULL)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (7, N'UX-дизайн', N'Основы пользовательского опыта', N'Статья о проектировании интерфейсов', CAST(N'2024-02-07' AS Date), 2, 7, 2)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (8, N'Базы данных', N'SQL и NoSQL', N'Обзор современных СУБД', CAST(N'2024-02-08' AS Date), 1, 10, NULL)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (9, N'Компьютерные сети', N'Протоколы и архитектура', N'Материал о сетевых технологиях', CAST(N'2024-02-09' AS Date), 2, 2, 4)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (10, N'Разработка игр', N'Введение в геймдев', N'Статья о создании игр', CAST(N'2024-02-10' AS Date), 1, 3, 5)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (11, N'Тестирование ПО', N'Основы QA', N'Материал о тестировании программ', CAST(N'2024-02-11' AS Date), 1, 7, 6)
INSERT [dbo].[Articles] ([ArticleID], [Title], [Summary], [Content], [Date], [StatusID], [AuthorID], [PartnerID]) VALUES (12, N'Администрирование Linux', N'Практическое руководство', N'Статья по управлению Linux-серверами', CAST(N'2024-02-12' AS Date), 2, 10, NULL)
SET IDENTITY_INSERT [dbo].[Articles] OFF
GO
SET IDENTITY_INSERT [dbo].[ArticleStatuses] ON 

INSERT [dbo].[ArticleStatuses] ([StatusID], [Status]) VALUES (1, N'Опубликована')
INSERT [dbo].[ArticleStatuses] ([StatusID], [Status]) VALUES (2, N'На проверке')
INSERT [dbo].[ArticleStatuses] ([StatusID], [Status]) VALUES (3, N'Отклонена')
SET IDENTITY_INSERT [dbo].[ArticleStatuses] OFF
GO
SET IDENTITY_INSERT [dbo].[Comments] ON 

INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (1, 1, 4, N'Отличная статья!', CAST(N'2024-02-01' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (2, 1, 5, N'Очень полезно', CAST(N'2024-02-01' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (3, 2, 6, N'Спасибо за материал', CAST(N'2024-02-02' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (4, 2, 7, N'Хорошо объяснено', CAST(N'2024-02-02' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (5, 3, 8, N'Не хватает примеров', CAST(N'2024-02-03' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (6, 3, 9, N'Актуальная тема', CAST(N'2024-02-03' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (7, 4, 10, N'Полезная информация', CAST(N'2024-02-04' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (8, 4, 4, N'Отлично написано', CAST(N'2024-02-04' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (9, 5, 5, N'Неинтересно', CAST(N'2024-02-05' AS Date), 1)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (10, 6, 6, N'Очень интересно', CAST(N'2024-02-06' AS Date), 1)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (11, 6, 7, N'Узнал много нового', CAST(N'2024-02-06' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (12, 7, 8, N'Статья короткая', CAST(N'2024-02-07' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (13, 8, 9, N'Отличный обзор', CAST(N'2024-02-08' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (14, 8, 4, N'Всё понятно и доступно', CAST(N'2024-02-08' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (15, 9, 5, N'Автор глупый', CAST(N'2024-02-09' AS Date), 1)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (16, 10, 6, N'Классная статья', CAST(N'2024-02-10' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (17, 10, 7, N'Понравилось', CAST(N'2024-02-10' AS Date), 0)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (18, 11, 8, N'Жду продолжения', CAST(N'2024-02-11' AS Date), 1)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (19, 12, 9, N'Писатель криворукий', CAST(N'2024-02-12' AS Date), 1)
INSERT [dbo].[Comments] ([CommentID], [ArticleID], [UserID], [Content], [Date], [IsDeleted]) VALUES (20, 12, 10, N'Спасибо автору', CAST(N'2024-02-12' AS Date), 0)
SET IDENTITY_INSERT [dbo].[Comments] OFF
GO
SET IDENTITY_INSERT [dbo].[Partners] ON 

INSERT [dbo].[Partners] ([PartnerID], [PartnerName], [ContactInfo]) VALUES (1, N'OpenAI', N'contact@openai.com')
INSERT [dbo].[Partners] ([PartnerID], [PartnerName], [ContactInfo]) VALUES (2, N'МАХ', N'info@yandex.com')
INSERT [dbo].[Partners] ([PartnerID], [PartnerName], [ContactInfo]) VALUES (3, N'Google', N'support@google.com')
INSERT [dbo].[Partners] ([PartnerID], [PartnerName], [ContactInfo]) VALUES (4, N'АО3', N'aws@amo.com')
INSERT [dbo].[Partners] ([PartnerID], [PartnerName], [ContactInfo]) VALUES (5, N'Meta', N'meta@meta.com')
INSERT [dbo].[Partners] ([PartnerID], [PartnerName], [ContactInfo]) VALUES (6, N'Яндекс', N'info@yandex.ru')
SET IDENTITY_INSERT [dbo].[Partners] OFF
GO
SET IDENTITY_INSERT [dbo].[Roles] ON 

INSERT [dbo].[Roles] ([RoleID], [RoleName]) VALUES (4, N'Автор')
INSERT [dbo].[Roles] ([RoleID], [RoleName]) VALUES (1, N'Администратор')
INSERT [dbo].[Roles] ([RoleID], [RoleName]) VALUES (2, N'Модератор')
INSERT [dbo].[Roles] ([RoleID], [RoleName]) VALUES (5, N'Пользователь')
INSERT [dbo].[Roles] ([RoleID], [RoleName]) VALUES (3, N'Редактор')
SET IDENTITY_INSERT [dbo].[Roles] OFF
GO
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (1, 1)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (1, 4)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (2, 2)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (3, 5)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (4, 3)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (5, 5)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (6, 3)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (7, 2)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (8, 3)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (9, 4)
INSERT [dbo].[UserRoles] ([UserID], [RoleID]) VALUES (10, 2)
GO
SET IDENTITY_INSERT [dbo].[Users] ON 

INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (1, N'admin', N'admin123', N'Администратор', N'admin@mail.com', CAST(N'2024-01-01' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (2, N'ivanov', N'pass123', N'Иван Иванов', N'ivan@mail.com', CAST(N'2024-01-05' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (3, N'petrov', N'qwerty', N'Пётр Петров', N'petr@mail.com', CAST(N'2024-01-06' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (4, N'anna', N'anna123', N'Анна Смирнова', N'anna@mail.com', CAST(N'2024-01-07' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (5, N'sergey', N'serg123', N'Сергей Кузнецов', N'serg@mail.com', CAST(N'2024-01-08' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (6, N'olga', N'olga123', N'Ольга Иванова', N'olga@mail.com', CAST(N'2024-01-09' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (7, N'max', N'max123', N'Максим Волков', N'max@mail.com', CAST(N'2024-01-10' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (8, N'kate', N'kate123', N'Екатерина Орлова', N'kate@mail.com', CAST(N'2024-01-11' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (9, N'dima', N'dima123', N'Дмитрий Соколов', N'dima@mail.com', CAST(N'2024-01-12' AS Date))
INSERT [dbo].[Users] ([UserID], [Login], [Password], [Username], [Email], [CreationDate]) VALUES (10, N'alex', N'alex123', N'Алексей Морозов', N'alex@mail.com', CAST(N'2024-01-13' AS Date))
SET IDENTITY_INSERT [dbo].[Users] OFF
GO
SET ANSI_PADDING ON
GO
/****** Object:  Index [UQ__Roles__737584F6FD9E052B]    Script Date: 27.02.2026 2:06:38 ******/
ALTER TABLE [dbo].[Roles] ADD  CONSTRAINT [UQ__Roles__737584F6FD9E052B] UNIQUE NONCLUSTERED 
(
	[RoleName] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, SORT_IN_TEMPDB = OFF, IGNORE_DUP_KEY = OFF, ONLINE = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
GO
SET ANSI_PADDING ON
GO
/****** Object:  Index [UQ__Users__5E55825BD2844DFA]    Script Date: 27.02.2026 2:06:38 ******/
ALTER TABLE [dbo].[Users] ADD  CONSTRAINT [UQ__Users__5E55825BD2844DFA] UNIQUE NONCLUSTERED 
(
	[Login] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, SORT_IN_TEMPDB = OFF, IGNORE_DUP_KEY = OFF, ONLINE = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
GO
ALTER TABLE [dbo].[Comments] ADD  CONSTRAINT [DF__Comments__Create__5AEE82B9]  DEFAULT (getdate()) FOR [Date]
GO
ALTER TABLE [dbo].[Comments] ADD  CONSTRAINT [DF__Comments__IsDele__5BE2A6F2]  DEFAULT ((0)) FOR [IsDeleted]
GO
ALTER TABLE [dbo].[Articles]  WITH CHECK ADD  CONSTRAINT [FK_Articles_ArticleStatuses] FOREIGN KEY([StatusID])
REFERENCES [dbo].[ArticleStatuses] ([StatusID])
GO
ALTER TABLE [dbo].[Articles] CHECK CONSTRAINT [FK_Articles_ArticleStatuses]
GO
ALTER TABLE [dbo].[Articles]  WITH CHECK ADD  CONSTRAINT [FK_Articles_Partners] FOREIGN KEY([PartnerID])
REFERENCES [dbo].[Partners] ([PartnerID])
GO
ALTER TABLE [dbo].[Articles] CHECK CONSTRAINT [FK_Articles_Partners]
GO
ALTER TABLE [dbo].[Comments]  WITH CHECK ADD  CONSTRAINT [FK_Comments_Articles] FOREIGN KEY([ArticleID])
REFERENCES [dbo].[Articles] ([ArticleID])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[Comments] CHECK CONSTRAINT [FK_Comments_Articles]
GO
ALTER TABLE [dbo].[Comments]  WITH CHECK ADD  CONSTRAINT [FK_Comments_Users] FOREIGN KEY([UserID])
REFERENCES [dbo].[Users] ([UserID])
GO
ALTER TABLE [dbo].[Comments] CHECK CONSTRAINT [FK_Comments_Users]
GO
ALTER TABLE [dbo].[UserRoles]  WITH CHECK ADD  CONSTRAINT [FK_UserRoles_Roles] FOREIGN KEY([RoleID])
REFERENCES [dbo].[Roles] ([RoleID])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[UserRoles] CHECK CONSTRAINT [FK_UserRoles_Roles]
GO
ALTER TABLE [dbo].[UserRoles]  WITH CHECK ADD  CONSTRAINT [FK_UserRoles_Users] FOREIGN KEY([UserID])
REFERENCES [dbo].[Users] ([UserID])
ON DELETE CASCADE
GO
ALTER TABLE [dbo].[UserRoles] CHECK CONSTRAINT [FK_UserRoles_Users]
GO
USE [master]
GO
ALTER DATABASE [ITForumDB] SET  READ_WRITE 
GO

