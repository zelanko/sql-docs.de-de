---
title: Namespace-URI-from-QName (XQuery) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Namespace-URI-from-QName-Funktion verwenden, um den Namespace-URI eines QName abzurufen.
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:namespace-uri-from-QName function
- namespace-uri-from-QName function
ms.assetid: 4ab3f003-2a3b-4268-9e88-b615e35701b2
author: rothja
ms.author: jroth
ms.openlocfilehash: 91174fa3ef113a7944ef02bb62e7088acd344f3e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85720035"
---
# <a name="functions-related-to-qnames---namespace-uri-from-qname"></a>Funktionen, die sich auf QNames beziehen – namespace-uri-from-QName
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  Gibt eine Zeichenfolge zurück, die den Namespace-URI des von *$arg*angegebenen QName darstellt. Das Ergebnis ist die leere Sequenz, wenn *$arg* die leere Sequenz ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
namespace-uri-from-QName($arg as xs:QName?) as xs:string?  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Ist der QName, dessen Namespace-URI zurückgegeben wurde.  
  
## <a name="examples"></a>Beispiele  
 Dieses Thema stellt XQuery-Beispiele für XML-Instanzen bereit, die in verschiedenen Spalten vom Typ **XML** in der AdventureWorks-Datenbank gespeichert sind.  
  
### <a name="a-retrieve-the-namespace-uri-from-a-qname"></a>A. Abrufen der Namespace-URI von einem QName  
 Ein funktionierendes Beispiel finden Sie unter [local-name-from-QName &#40;XQuery&#41;](../xquery/functions-related-to-qnames-local-name-from-qname.md).  
  
### <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Die **Namespace-URI-from-QName ()-** Funktion gibt Instanzen von xs: String anstelle von xs: anyURI zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen im Zusammenhang mit QNames &#40;XQuery-&#41;](https://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
