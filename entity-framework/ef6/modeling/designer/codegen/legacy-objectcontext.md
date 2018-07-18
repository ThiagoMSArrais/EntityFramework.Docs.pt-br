---
title: Revertendo para o ObjectContext no Entity Framework Designer - EF6
author: divega
ms.date: 2016-10-23
ms.prod: entity-framework
ms.author: divega
ms.manager: avickers
ms.technology: entity-framework-6
ms.topic: article
ms.assetid: 36550569-a1de-47cb-ba6d-544794ffd500
caps.latest.revision: 3
ms.openlocfilehash: 17fa6538cf5e92f59ab72376af96ad65c640a085
ms.sourcegitcommit: f05e7b62584cf228f17390bb086a61d505712e1b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/08/2018
ms.locfileid: "39119838"
---
# <a name="reverting-to-objectcontext-in-entity-framework-designer"></a>Revertendo para o ObjectContext no Entity Framework Designer
Com a versão anterior do Entity Framework um modelo criado com o EF Designer geraria um contexto que é derivada de ObjectContext e classes de entidade derivam de EntityObject.

Começando com o EF4.1 é recomendável alternar para um modelo de geração de código que gera um contexto derivado de DbContext e POCO classes de entidade.

No Visual Studio 2012 você obtém o código de DbContext gerado por padrão para todos os novos modelos criados com o EF Designer. Os modelos existentes continuarão gerar o código de ObjectContext com base, a menos que você decidir trocar para o gerador de código com base do DbContext.

## <a name="reverting-back-to-objectcontext-code-generation"></a>Reverter para a geração de código de ObjectContext

### <a name="1-disable-dbcontext-code-generation"></a>1. Desabilitar a geração de código de DbContext

Geração das classes derivadas de DbContext e POCO é manipulada por dois arquivos. TT no projeto, se você expandir o arquivo. edmx no Gerenciador de soluções, você verá esses arquivos. Exclua ambos os arquivos do seu projeto.

![CodeGenFiles](~/ef6/media/codegenfiles.png)

Se você estiver usando o VB.NET você precisará selecionar o **Show All Files** botão para ver os arquivos aninhados.

![Exibtodosarqs](~/ef6/media/showallfiles.png)

### <a name="2-re-enable-objectcontext-code-generation"></a>2. Habilite novamente a geração de código de ObjectContext

Abrir modelo no Designer de EF, clique com o botão direito em uma seção em branco da superfície do design e selecione **propriedades**.

Em que a alteração da janela de propriedades de **estratégia de geração de código** de **None** para **padrão**.

![CodeGenStrategy](~/ef6/media/codegenstrategy.png)