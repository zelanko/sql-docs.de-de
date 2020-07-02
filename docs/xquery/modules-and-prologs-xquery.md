---
title: Module und Prologs (XQuery) | Microsoft-Dokumentation
description: Erfahren Sie, welche Spezifikationen beim Deklarieren eines Namespace in einem XQuery-Prolog nicht unterstützt werden.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, prolog
- prolog
ms.assetid: 0f17b4a4-6234-41d4-a996-6db4e27bff7e
author: rothja
ms.author: jroth
ms.openlocfilehash: c7d982e8c944ff1c596dfa4178ce613ec3be709e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85759489"
---
# <a name="modules-and-prologs-xquery"></a>Module und Prologe (XQuery)
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  Der [XQuery-Prolog](../xquery/modules-and-prologs-xquery-prolog.md) ist eine Reihe von Namespace Deklarationen. Wenn Sie den Namespace im Prolog verwenden, können Sie ein Präfix für die Namespaceeinbindung angeben und das Präfix im Abfragehauptteil verwenden.  
  
## <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden XQuery-Spezifikationen werden in dieser Implementierung nicht unterstützt:  
  
-   Moduldeklaration (`version`)  
  
-   Moduldeklaration (`module namespace`)  
  
-   Xmpspacedeclaration ( `xmlspace` )  
  
-   Standardsortierungsdeklaration (`declare default collation`)  
  
-   Basis-URI-Deklaration (`declare base-uri`)  
  
-   Konstruktionsdeklaration (`declare construction`)  
  
-   Standardreihenfolgendeklaration (`declare ordering`)  
  
-   Schemaimport (`import schema namespace`)  
  
-   Modulimport (`import module`)  
  
-   Variable Deklaration im Prolog (`declare variable`)  
  
-   Funktionsdeklaration (`declare function`)  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [XQuery-Prolog](../xquery/modules-and-prologs-xquery-prolog.md)  
 Beschreibt den XQuery-Prolog.  
  
## <a name="see-also"></a>Weitere Informationen  
 [XQuery-Sprachreferenz &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
