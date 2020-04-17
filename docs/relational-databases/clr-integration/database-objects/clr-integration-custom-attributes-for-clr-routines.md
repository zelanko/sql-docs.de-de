---
title: Benutzerdefinierte Attribute für CLR-Routinen | Microsoft Docs
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
ms.openlocfilehash: a32a606f73858ede15569d1ade891ad2ce1c69a5
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487952"
---
# <a name="clr-integration-custom-attributes-for-clr-routines"></a>CLR-Integration: Benutzerdefinierte Attribute für CLR-Routinen
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Die aufgeführten Attribute können auf CLR-Routinen (Common Language Runtime), benutzerdefinierte Typen und benutzerdefinierte [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Aggregate angewendet werden, die in registriert sind. Wenn das Attribut nicht angewendet wird, nimmt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den Standardwert an. Die aufgeführten Attribute sind im **Microsoft.SqlServer.Server-Namespace** definiert.  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>Das 'SqlUserDefinedAggregate'-Attribut  
 Das **SqlUserDefinedAggregate-Attribut** gibt an, dass die Methode als benutzerdefiniertes Aggregat registriert werden soll. Jedem benutzerdefinierten Aggregat muss dieses Attribut angefügt werden.  
  
 Weitere Informationen finden Sie unter [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626).  
  
## <a name="the-sqlfunction-attribute"></a>Das 'SqlFunction'-Attribut  
 Das **SqlFunction-Attribut** gibt an, dass die Methode als Funktion registriert werden soll, wobei die entsprechenden Funktionsattribute festgelegt sind.  
  
 Weitere Informationen finden Sie unter [SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019).  
  
## <a name="the-sqlfacet-attribute"></a>Das 'SqlFacet'-Attribut  
 Das **SqlFacet-Attribut** wird verwendet, um Informationen über den Rückgabetyp eines benutzerdefinierten Typausdrucks (UDT) zurückzugeben.  
  
 Weitere Informationen finden Sie unter [SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020).  
  
## <a name="the-sqlprocedure-attribute"></a>Das 'SqlProcedure'-Attribut  
 Das **SqlProcedure-Attribut** gibt an, dass die Methode als gespeicherte Prozedur registriert werden soll. Dieses Attribut wird nur von Visual Studio verwendet, um die angegebene Methode automatisch als gespeicherte Prozedur zu registrieren. Sie wird nicht von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet.  
  
 Weitere Informationen finden Sie unter [SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021).  
  
## <a name="the-sqltrigger-attribute"></a>Das 'SqlTrigger'-Attribut  
 Das **SqlTrigger-Attribut** gibt an, dass die Methode als Trigger registriert werden soll.  
  
 Weitere Informationen finden Sie unter [SqlTriggerContext](https://go.microsoft.com/fwlink/?LinkId=128022) und [SqlTriggerAttribute](https://go.microsoft.com/fwlink/?LinkId=203898).  
  
## <a name="the-sqluserdefinedtypeattribute"></a>Das 'SqlUserDefinedTypeAttribute'-Attribut  
 Sie können das SqlUserDefinedTypeAttribute-Attribut in eine Klassendefinition in der Assembly übernehmen. Es bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] einen benutzerdefinierten Typ erstellt, der an die Klassendefinition mit diesem benutzerdefinierten Attribut gebunden ist.  
  
 Weitere Informationen finden Sie unter [SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024).  
  
## <a name="the-sqlmethod-attribute"></a>Das 'SqlMethod'-Attribut  
 Das **SqlMethod-Attribut** wird verwendet, um die Determinismus- und Datenzugriffseigenschaften einer Methode oder einer Eigenschaft in einer UDT anzugeben.  
  
 Weitere Informationen finden Sie unter [SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte CLR-Aggregate](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [Benutzerdefinierte CLR-Funktionen](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Benutzerdefinierte CLR-Typen](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [GESPEICHERTe CLR-Prozeduren](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [CLR-Trigger](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)  
  
  
