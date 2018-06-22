---
title: Escrevendo um provedor de banco de dados - Core EF
author: anmiller
ms.author: divega
ms.date: 10/27/2016
ms.assetid: 1165e2ec-e421-43fc-92ab-d92f9ab3c494
ms.technology: entity-framework-core
uid: core/providers/writing-a-provider
ms.openlocfilehash: 4bddf5858ab2c6b2fd22571a20edb3f7c85e2853
ms.sourcegitcommit: b2d94cebdc32edad4fecb07e53fece66437d1b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
ms.locfileid: "29678954"
---
# <a name="writing-a-database-provider"></a><span data-ttu-id="44ec1-102">Escrevendo um provedor de banco de dados</span><span class="sxs-lookup"><span data-stu-id="44ec1-102">Writing a Database Provider</span></span>

<span data-ttu-id="44ec1-103">Para obter informações sobre como escrever um provedor de banco de dados do Entity Framework Core, consulte [para que você deseja gravar um provedor EF Core](https://blog.oneunicorn.com/2016/11/11/so-you-want-to-write-an-ef-core-provider/) por [Arthur Vickers](https://github.com/ajcvickers).</span><span class="sxs-lookup"><span data-stu-id="44ec1-103">For information about writing an Entity Framework Core database provider, see [So you want to write an EF Core provider](https://blog.oneunicorn.com/2016/11/11/so-you-want-to-write-an-ef-core-provider/) by [Arthur Vickers](https://github.com/ajcvickers).</span></span>

<span data-ttu-id="44ec1-104">A base de código EF Core é o código-fonte aberto e contém vários provedores de banco de dados que podem ser usados como uma referência.</span><span class="sxs-lookup"><span data-stu-id="44ec1-104">The EF Core code base is open source and contains several database providers that can be used as a reference.</span></span> <span data-ttu-id="44ec1-105">Você pode encontrar o código-fonte em https://github.com/aspnet/EntityFrameworkCore.</span><span class="sxs-lookup"><span data-stu-id="44ec1-105">You can find the source code at https://github.com/aspnet/EntityFrameworkCore.</span></span>

## <a name="the-providers-beware-label"></a><span data-ttu-id="44ec1-106">O rótulo cuidado com provedores</span><span class="sxs-lookup"><span data-stu-id="44ec1-106">The providers-beware label</span></span>

<span data-ttu-id="44ec1-107">Quando você começar a trabalhar em um provedor, observe o [ `providers-beware` ](https://github.com/aspnet/EntityFrameworkCore/labels/providers-beware) rótulo em nossos GitHub problemas e solicitações pull.</span><span class="sxs-lookup"><span data-stu-id="44ec1-107">Once you begin work on a provider, watch for the [`providers-beware`](https://github.com/aspnet/EntityFrameworkCore/labels/providers-beware) label on our GitHub issues and pull requests.</span></span> <span data-ttu-id="44ec1-108">Usamos este rótulo para identificar as alterações que podem afetar os gravadores de provedor.</span><span class="sxs-lookup"><span data-stu-id="44ec1-108">We use this label to identify changes that may impact provider writers.</span></span>

## <a name="suggested-naming-of-third-party-providers"></a><span data-ttu-id="44ec1-109">Sugerido nomeação de provedores de terceiros</span><span class="sxs-lookup"><span data-stu-id="44ec1-109">Suggested naming of third party providers</span></span>

<span data-ttu-id="44ec1-110">Sugerimos usando a nomenclatura seguintes pacotes do NuGet.</span><span class="sxs-lookup"><span data-stu-id="44ec1-110">We suggest using the following naming for NuGet packages.</span></span> <span data-ttu-id="44ec1-111">Isso é consistente com os nomes de pacotes entregues pela equipe do EF Core.</span><span class="sxs-lookup"><span data-stu-id="44ec1-111">This is consistent with the names of packages delivered by the EF Core team.</span></span>

`<Optional project/company name>.EntityFrameworkCore.<Database engine name>`

<span data-ttu-id="44ec1-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="44ec1-112">For example:</span></span>
* `Microsoft.EntityFrameworkCore.SqlServer`
* `Npgsql.EntityFrameworkCore.PostgreSQL`
* `EntityFrameworkCore.SqlServerCompact40`
