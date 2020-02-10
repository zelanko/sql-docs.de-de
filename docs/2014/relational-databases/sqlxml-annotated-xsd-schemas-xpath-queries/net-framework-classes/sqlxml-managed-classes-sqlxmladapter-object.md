---
title: SqlXmlAdapter-Objekt (verwaltete SQLXML-Klassen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b339e67b07ddb4168f9922c22e620eb2fa10d85e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66014933"
---
# <a name="sqlxmladapter-object-sqlxml-managed-classes"></a>SqlXmlAdapter-Objekt (Verwaltete SQLXML-Klassen)
  Dieses Objekt stellt Methoden bereit, welche die Interaktion mit dem Dataset in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework erleichtern. Ein funktionierendes Beispiel finden Sie unter [zugreifen auf die SQLXML-Funktionalität in der .NET-Umgebung](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 Das SqlXmlAdapter-Objekt unterstützt diese Methoden:  
  
 void Fill (DataSet DS)  
 Füllt das Dataset in .NET Framework mit den von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] abgerufenen XML-Daten.  
  
 void Update (DataSet-DS)  
 Übernimmt Updates aus den Daten im Dataset und wendet sie auf Datensätze in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an.  
  
 Das SqlXmlAdapter-Objekt unterstützt diese Konstruktoren:  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SqlXmlCommand-Objekt &#40;verwalteten SQLXML-Klassen&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)   
 [SqlXmlParameter-Objekt &#40;verwalteten SQLXML-Klassen&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
