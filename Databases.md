####


```C#
CREATE TABLE Contacts (
    [ContactId]    INT              IDENTITY (1, 1) NOT NULL,
    [FullName]     NVARCHAR(250)    NOT NULL,
    [CompanyName]  NVARCHAR(250)    NULL,
    [Position]     NVARCHAR(250)    NULL,
    [Country]      NVARCHAR(150)    NULL,
    [Email]        VARCHAR (250)    NOT NULL,
    [GuID]         UNIQUEIDENTIFIER DEFAULT (newid()) NOT NULL,
    [DateInserted] DATETIME2 (7)    CONSTRAINT [DF_Contacts_DateInserted] DEFAULT (getdate()) NOT NULL,
    CONSTRAINT [PK_Contacts] PRIMARY KEY CLUSTERED ([ContactId] ASC)
);


CREATE TABLE [dbo].[Contacts] (
    [ContactId]    INT              IDENTITY (1, 1) NOT NULL,
    [FullName]     VARCHAR(250)    NOT NULL,
    [CompanyName]  VARCHAR(250)    NULL,
    [Position]     VARCHAR(250)    NULL,
    [Country]      VARCHAR(150)    NULL,
    [Email]        VARCHAR (250)    NOT NULL,
    [GuID]         UNIQUEIDENTIFIER DEFAULT (newid()) NOT NULL,
    [DateInserted] DATETIME2 (7)    CONSTRAINT [DF_Contacts_DateInserted] DEFAULT (getdate()) NOT NULL,
    CONSTRAINT [PK_Contacts] PRIMARY KEY CLUSTERED ([ContactId] ASC)
);

CREATE TABLE [dbo].[EmailLists] (
    [EmailListID]   INT           IDENTITY (1, 1) NOT NULL,
    [EmailListName] VARCHAR (250) NOT NULL,
    CONSTRAINT [PK_dbo.EmailLists] PRIMARY KEY CLUSTERED ([EmailListID] ASC)
);



CREATE TABLE [dbo].[EmailListContacts] (
    [EmailListID] INT NOT NULL,
 [ContactID]   INT NOT NULL,
    CONSTRAINT [PK_dbo.EmailListContacts] PRIMARY KEY CLUSTERED ([EmailListID] ASC, [ContactID] ASC),
    CONSTRAINT [FK_dbo.EmailListContacts_dbo.Contacts_Contact_Id] FOREIGN KEY ([ContactID]) REFERENCES [dbo].[Contacts] ([ContactId]) ON DELETE CASCADE,
    CONSTRAINT [FK_dbo.EmailListContacts_dbo.EmailLists_EmailList_ID] FOREIGN KEY ([EmailListID]) REFERENCES [dbo].[EmailLists] ([EmailListID]) ON DELETE CASCADE
);



CREATE TABLE [dbo].[Templates] (
    [TemplateId]   INT            IDENTITY (1, 1) NOT NULL,
    [TemplateName] NVARCHAR (100) NOT NULL,
    PRIMARY KEY CLUSTERED ([TemplateId] ASC)
);
```
