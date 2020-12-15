---
title: Einführung in DiffGrams für SQLXML 4.0
description: Erfahren Sie mehr über das Format, die Anmerkungen und die Verarbeitungslogik der Diffgrams in SQLXML 4,0.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotations [SQLXML]
- DiffGrams [SQLXML], about DiffGrams
ms.assetid: 1902d67f-baf3-46e6-a36c-b24b5ba6f8ea
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 66a58dfb19cf8f53f775bac663d5ba3e6147711b
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97414945"
---
# <a name="introduction-to-diffgrams-in-sqlxml-40"></a>Einführung in DiffGrams für SQLXML 4.0
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Dieses Thema bietet eine kurze Einführung in DiffGrams.  
  
## <a name="diffgram-format"></a>DiffGram-Format  
 Das allgemeine DiffGram-Format sieht folgendermaßen aus:  
  
```  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
   <DataInstance>  
      ...  
   </DataInstance>  
   [<diffgr:before>  
        ...  
   </diffgr:before>]  
  
   [<diffgr:errors>  
        ...  
   </diffgr:errors>]  
</diffgr:diffgram>  
```  
  
 Das DiffGram-Format besteht aus den folgenden Blöcken:  
  
 **\<DataInstance>**  
 Der Name dieses Elements, **DataInstance**, wird zur Erläuterung in dieser Dokumentation verwendet. Wenn beispielsweise das DiffGram-Objekt aus einem Dataset im .NET Framework generiert wurde, wird der Wert der **Name** -Eigenschaft des Datasets als Name dieses Elements verwendet. Dieser Block enthält nach der Änderung alle relevanten Daten, möglicherweise auch die Daten, die nicht geändert wurden. Die DiffGram-Verarbeitungslogik ignoriert die Elemente in diesem Block, für die das **diffgr: hasChanges** -Attribut nicht angegeben ist.  
  
 **\<diffgr:before>**  
 Dieser optionale Block enthält die ursprünglichen Datensatzinstanzen (Elemente), die aktualisiert oder gelöscht werden müssen. Alle Datenbanktabellen, die vom DiffGram geändert (aktualisiert oder gelöscht) werden, müssen im-Block als Elemente der obersten Ebene angezeigt werden **\<before>** .  
  
 **\<diffgr:errors>**  
 Dieser optionale Block wird von der DiffGram-Verarbeitungslogik ignoriert.  
  
## <a name="diffgram-annotations"></a>DiffGram-Anmerkungen  
 Diese Anmerkungen werden im DiffGram-Namespace **"urn: Schemas-Microsoft-com: XML-DiffGram-01"** definiert:  
  
 **id**  
 Dieses Attribut wird verwendet, um die Elemente in den **\<before>** -und-Blöcken zu koppeln **\<DataInstance>** .  
  
 **hasChanges**  
 Bei einem INSERT-oder Update-Vorgang muss das DiffGram-Attribut dieses Attribut mit dem **eingefügten** oder **geänderten** Wert angeben. Wenn dieses Attribut nicht vorhanden ist, wird das entsprechende Element in der **\<DataInstance>** von der Verarbeitungslogik ignoriert, und es werden keine Updates durchgeführt. Arbeitsbeispiele finden Sie unter [DiffGram-Beispiele &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).  
  
 **parentID**  
 Mit diesem Attribut werden Über-/Unterordnungsbeziehungen unter den Elementen des DiffGrams angegeben. Dieses Attribut wird nur im- \<before> Block angezeigt. Es wird von SQLXML beim Übernehmen von Updates genutzt. Anhand der Über-/Unterordnungsbeziehungen wird die Reihenfolge bestimmt, in der die Elemente des DiffGrams verarbeitet werden.  
  
## <a name="understanding-the-diffgram-processing-logic"></a>Grundlegendes zur DiffGram-Verarbeitungslogik  
 Die DiffGram-Verarbeitungslogik verwendet bestimmte Regeln, um zu bestimmen, ob es sich bei einem Vorgang um einen Einfüge-, Aktualisieren- oder Löschvorgang handelt. Diese Regeln werden in der folgenden Tabelle beschrieben.  
  
|Vorgang|BESCHREIBUNG|  
|---------------|-----------------|  
|Einfügen|Ein DiffGram zeigt einen Einfügevorgang an, wenn ein Element im- **\<DataInstance>** Block, jedoch nicht im entsprechenden **\<before>** -Block angezeigt wird, und das **diffgr: hasChanges** -Attribut (**diffgr: hasChanges = eingefügt**) für das-Element angegeben wird. In diesem Fall fügt das DiffGram die Daten Satz Instanz, die im-Block angegeben ist, **\<DataInstance>** in die Datenbank ein.<br /><br /> Wenn das **diffgr: hasChanges** -Attribut nicht angegeben wird, wird das-Element von der Verarbeitungslogik ignoriert, und es wird kein INSERT-Vorgang ausgeführt. Arbeitsbeispiele finden Sie unter [DiffGram-Beispiele &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).|  
|Aktualisieren|Das DiffGram zeigt einen Update Vorgang an, wenn ein Element im- \<before> Block vorhanden ist, für das ein entsprechendes-Element im-Block vorhanden ist (d. **\<DataInstance>** h. beide-Elemente verfügen über ein **diffgr: ID** -Attribut mit demselben Wert) und das **diffgr: hasChanges** -Attribut mit dem Wert, der für das-Element im-Block **geändert** wurde **\<DataInstance>** .<br /><br /> Wenn das **diffgr: hasChanges** -Attribut für das-Element im-Block nicht angegeben wird **\<DataInstance>** , wird von der Verarbeitungslogik ein Fehler zurückgegeben. Arbeitsbeispiele finden Sie unter [DiffGram-Beispiele &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).<br /><br /> Wenn **diffgr: parameted im-** Block angegeben wird **\<before>** , wird die über-/Unterordnungsbeziehung der Elemente, die von der **parameentid** angegeben werden, verwendet, um die Reihenfolge zu bestimmen, in der die Datensätze aktualisiert werden.|  
|Löschen|Ein DiffGram gibt einen Löschvorgang an, wenn ein Element im- **\<before>** Block, jedoch nicht im entsprechenden-Block angezeigt wird **\<DataInstance>** . In diesem Fall löscht das DiffGram die Daten Satz Instanz, die im- **\<before>** Block aus der Datenbank angegeben wird. Arbeitsbeispiele finden Sie unter [DiffGram-Beispiele &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/diffgram/diffgram-examples-sqlxml-4-0.md).<br /><br /> Wenn **diffgr: parameted im-** Block angegeben wird **\<before>** , wird die über-/Unterordnungsbeziehung der Elemente, die von der **parameentid** angegeben werden, verwendet, um die Reihenfolge zu bestimmen, in der Datensätze gelöscht werden.|  
  
> [!NOTE]  
>  DiffGrams können keine Parameter übergeben werden.  
  
  
