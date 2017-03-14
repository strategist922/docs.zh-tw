---
title: "dotnet-sln 命令 | Microsoft Docs"
description: "dotnet-sln 命令提供方便在方案檔中新增、移除及列出專案的選項。"
keywords: "dotnet-sln, CLI, CLI 命令, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e5a72d3e-c14b-4b0a-a978-c5e54a0988c6
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 84c2a9cab36dcfa76f90d75c83f4988ba441b0a8
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-sln"></a>dotnet-sln

## <a name="name"></a>名稱

`dotnet-sln` - 修改.NET Core 方案檔。

## <a name="synopsis"></a>概要

```
dotnet sln [<solution_name>] add <project> <project>
dotnet sln [<solution_name>] add **/**
dotnet sln [<solution_name>] remove <project> <project>
dotnet sln [<solution_name>] remove **/**
dotnet sln [<solution_name>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>說明

`dotnet sln` 命令提供方便在方案檔中新增、移除及列出專案的方式。

## <a name="commands"></a>命令

`add <project>`

`add **/*`

將一個專案或多個專案加入至方案檔。 Unix/Linux 型終端機上支援 Glob 模式。

`remove <project>`

`remove **/*`

從方案檔中移除一個專案或多個專案。 Unix/Linux 型終端機上支援 Glob 模式。

`list`

列出方案檔中的所有專案。

## <a name="arguments"></a>引數

`solution_name`

要使用的方案檔。 如果未指定，命令會在目前的目錄中搜尋一個方案檔。 如果目錄中有多個方案檔，請務必指定一個方案檔。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

## <a name="examples"></a>範例

將專案加入至方案：

`dotnet sln todo.sln add todo-app/todo-app.csproj`

將專案加入至目前目錄中的方案︰

`dotnet sln add todo-app.csproj`

移除方案中的專案：

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

使用 Glob 模式將多個專案加入至方案︰

`dotnet sln add **/**/*.fsproj`
