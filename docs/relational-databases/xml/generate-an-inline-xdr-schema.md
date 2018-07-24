---
title: Generieren eines XDR-Inlineschemas | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- XDR schemas [SQL Server]
- inline XDR schema generation [SQL Server]
- XMLDATA option
- FOR XML clause, inline XDR schema generation
ms.assetid: 2a40d617-9724-4f7d-80a4-a85c702f14d0
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7aec8be09b1ecd5faed258532d6e770c8720308a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38028848"
---
# <a name="generate-an-inline-xdr-schema"></a>Generieren eines XDR-Inlineschemas
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Von der **XMLDATA** -Direktive in FOR XML wird ein XDR-Inlineschema zusammen mit dem Abfrageergebnis zurückgegeben. Allerdings unterstützt das XDR-Schema nicht alle neuen Datentypen und anderen Erweiterungen, die in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen eingeführt wurden. Stattdessen können Sie ein XSD-Inlineschema mithilfe der [XMLSCHEMA-Direktive](../../relational-databases/xml/generate-an-inline-xsd-schema.md)anfordern.  
  
> [!IMPORTANT]  
>  Die XMLDATA-Direktive zur FOR XML-Option ist veraltet. Verwenden Sie XSD-Generierung für RAW- und AUTO-Modus. Es gibt keinen Ersatz für die XMLDATA-Direktive im EXPLICIT-Modus. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Beachten Sie auch folgende Hinweise zur XDR-Inlineschemaunterstützung:  
  
-   Wenn das FOR XML-Abfrageergebnis Spalten vom Typ **xml** enthält und ein XDR-Inlineschema anfordert, wird ein Fehler zurückgegeben. Inline-XDR unterstützt diese Typen nicht.  
  
-   Die Typen **(n)varchar(max)** und **(n)varbinary(max)** werden **(n)varchar(n)** bzw. **varbinary(n)** zugeordnet.  
  
-   Wenn der Kompatibilitätsmodus auf 90 oder höher festgelegt ist, werden **timestamp** -Werte als **varbinary(8)** angesehen, wie Binärdaten behandelt und folgendermaßen zurückgegeben:  
  
    -   Base 64-Codierung wird verwendet, wenn **binary base64** angegeben wird.  
  
    -   URL-Codierung wird im AUTO-Modus verwendet, wenn **binary base64** nicht angegeben wurde.  
  
  
