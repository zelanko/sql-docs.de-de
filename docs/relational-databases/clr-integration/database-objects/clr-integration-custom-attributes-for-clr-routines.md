---
title: Benutzerdefinierte Attribute für CLR-Routinen | Microsoft-Dokumentation
description: Benutzerdefinierte Attribute können auf CLR-Routinen, benutzerdefinierte Typen und benutzerdefinierte Aggregate angewendet werden, die in Microsoft SQL Server registriert sind.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- SqlFacet attribute
- SqlTrigger attribute
- SqlProcedure attribute
- custom attributes [CLR integration]
- SqlUserDefinedAggregate attribute
- attributes [CLR integration]
- SqlMethod attribute
- SqlFunction attribute
- common language runtime [SQL Server], attributes
- SqlUserDefinedTypeAttribute attribute
ms.assetid: 95069d22-b05d-4670-b053-15ee2a664e33
author: rothja
ms.author: jroth
ms.openlocfilehash: bad209c4ddb516167b8048ae73680bc9ea59cc05
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810805"
---
# <a name="clr-integration-custom-attributes-for-clr-routines"></a>CLR-Integration: Benutzerdefinierte Attribute für CLR-Routinen
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  Die aufgelisteten Attribute können auf Common Language Runtime (CLR)-Routinen, benutzerdefinierte Typen und benutzerdefinierte Aggregate angewendet werden, die in registriert sind [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Wenn das Attribut nicht angewendet wird, nimmt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den Standardwert an. Die aufgelisteten Attribute werden im **Microsoft. SqlServer. Server** -Namespace definiert.  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>Das 'SqlUserDefinedAggregate'-Attribut  
 Das **SqlUserDefinedAggregate** -Attribut gibt an, dass die Methode als benutzerdefiniertes Aggregat registriert werden soll. Jedem benutzerdefinierten Aggregat muss dieses Attribut angefügt werden.  
  
 Weitere Informationen finden Sie unter [SqlUserDefinedAggregateAttribute](/dotnet/api/microsoft.sqlserver.server.sqluserdefinedaggregateattribute).  
  
## <a name="the-sqlfunction-attribute"></a>Das 'SqlFunction'-Attribut  
 Das **SqlFunction** -Attribut gibt an, dass die Methode als Funktion registriert werden soll, wobei die entsprechenden Funktions Attribute festgelegt sind.  
  
 Weitere Informationen finden Sie unter [SqlFunctionAttribute](/dotnet/api/microsoft.sqlserver.server.sqlfunctionattribute).  
  
## <a name="the-sqlfacet-attribute"></a>Das 'SqlFacet'-Attribut  
 Das **sqlface-Attribut** wird verwendet, um Informationen zum Rückgabetyp eines benutzerdefinierten Typs (User-Defined Type, UDT)-Ausdruck zurückzugeben.  
  
 Weitere Informationen finden Sie unter [sqlfaketattribute](/dotnet/api/microsoft.sqlserver.server.sqlfacetattribute).  
  
## <a name="the-sqlprocedure-attribute"></a>Das 'SqlProcedure'-Attribut  
 Das **SqlProcedure** -Attribut gibt an, dass die Methode als gespeicherte Prozedur registriert werden soll. Dieses Attribut wird nur von Visual Studio verwendet, um die angegebene Methode automatisch als gespeicherte Prozedur zu registrieren. Sie wird nicht von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet.  
  
 Weitere Informationen finden Sie unter [SqlProcedureAttribute](/dotnet/api/microsoft.sqlserver.server.sqlprocedureattribute).  
  
## <a name="the-sqltrigger-attribute"></a>Das 'SqlTrigger'-Attribut  
 Das **sqllock** -Attribut gibt an, dass die Methode als ein-Fehler registriert werden soll.  
  
 Weitere Informationen finden Sie unter [SqlTriggerContext](/dotnet/api/microsoft.sqlserver.server.sqltriggercontext) und [SqlTriggerAttribute](/dotnet/api/microsoft.sqlserver.server.sqltriggerattribute).  
  
## <a name="the-sqluserdefinedtypeattribute"></a>Das 'SqlUserDefinedTypeAttribute'-Attribut  
 Sie können das SqlUserDefinedTypeAttribute-Attribut in eine Klassendefinition in der Assembly übernehmen. Es bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einen benutzerdefinierten Typ erstellt, der an die Klassendefinition mit diesem benutzerdefinierten Attribut gebunden ist.  
  
 Weitere Informationen finden Sie unter [SqlUserDefinedTypeAttribute](/dotnet/api/microsoft.sqlserver.server.sqluserdefinedtypeattribute).  
  
## <a name="the-sqlmethod-attribute"></a>Das 'SqlMethod'-Attribut  
 Das **SqlMethod** -Attribut wird verwendet, um die Determinismus-und Datenzugriffs Eigenschaften einer Methode oder einer Eigenschaft in einem UDT anzugeben.  
  
 Weitere Informationen finden Sie unter [SqlMethodAttribute](/dotnet/api/microsoft.sqlserver.server.sqlmethodattribute).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte CLR-Aggregate](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [Benutzerdefinierte CLR-Funktionen](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Benutzerdefinierte CLR-Typen](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Gespeicherte CLR-Prozeduren](/dotnet/framework/data/adonet/sql/clr-stored-procedures)   
 [CLR-Trigger](/dotnet/framework/data/adonet/sql/clr-triggers)  
  
