---
title: Initialisieren von Objekten benutzerdefinierter Assemblys | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- initializing custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], initializing
- OnInit method
ms.assetid: 26fd74dc-d02f-40f7-aeb3-50ce05e9e6b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 97ee8e554fa246848b64ebafb0961f35d65f15c9
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60155691"
---
# <a name="initializing-custom-assembly-objects"></a>Initialisieren von Objekten benutzerdefinierter Assemblys
  In einigen Fällen müssen Sie die Werte der Eigenschaften und Felder in Ihren benutzerdefinierten Assemblyklassen beim Instanziieren initialisieren. Wahrscheinlich müssen Sie die benutzerdefinierten Klassen mit den Werten initialisieren, die Ihnen von den globalen Objektauflistungen des Berichts zur Verfügung stehen. Hierzu überschreiben Sie die **OnInit**-Methode des **Code**-Objekts eines Berichts. Verwenden Sie das **Code**-Element der Berichtsdefinition, um auf **OnInit** zuzugreifen. Es gibt zwei Techniken zum Initialisieren von Eigenschaft oder Feldwerte der Klassen in einer benutzerdefinierten Assembly, die Sie in Ihrem Bericht verwenden möchten: Sie können entweder deklarieren und erstellen Sie eine neue Instanz Ihrer Klasse verwenden **OnInit**, oder Sie rufen eine öffentlich verfügbare Methode mit **OnInit**.  
  
## <a name="global-object-collections-and-initialization"></a>Globale Objektauflistungen und Initialisierung  
 Zum Initialisieren der benutzerdefinierten Klassenvariablen stehen Ihnen mehrere Auflistungen zur Verfügung. Sie können die **Globals**-Auflistung und **die User**-Auflistung verwenden. Die Auflistungen **Parameters**, **Fields** und **ReportItems** stehen Ihnen zum Zeitpunkt des Berichtslebensdauerzyklus nicht zur Verfügung, wenn die **OnInit**-Methode aufgerufen wird. Sie müssen den **Report**-Objektverweis einschließen, um die freigegebenen Auflistungen **Globals** oder **User** zu verwenden. Wenn Sie beispielsweise Ihre benutzerdefinierte Klasse ausgehend von der aktuellen Sprache des Benutzers initialisieren möchten, der auf den Bericht zugreift, könnte Ihr **Code**-Element folgendermaßen aussehen:  
  
```  
<Code>  
   Dim m_myClass As MyClass  
  
   Protected Overrides Sub OnInit()  
      m_myClass = new MyClass(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 Eine Möglichkeit, die Eigenschaften- und Feldwerte einer Klasse zu initialisieren (wie bereits zuvor gezeigt), besteht darin, die neue Klasse zu deklarieren und eine neue Instanz davon zu erstellen, indem Sie einen überschriebenen Konstruktor aufrufen.  
  
 Eine andere Möglichkeit zur Initialisierung von Eigenschaften- und Feldwerten in den Klassen Ihrer benutzerdefinierten Assemblys besteht im Aufrufen einer öffentlich verfügbaren Methode, die Sie von der **OnInit**-Methode aus definieren. Sie müssen zuerst in der Berichtsdefinitionsdatei einen Instanznamen für die Klasse hinzufügen. Sobald Sie den entsprechenden Assemblyverweis und den Instanznamen hinzugefügt haben, können Sie die Initialisierungsmethode aufrufen, um die Eigenschaften- und Feldwerte für Ihre Klasse zu initialisieren. Ihre **OnInit**-Methode könnte folgendermaßen aussehen:  
  
```  
<Code>  
   Protected Overrides Sub OnInit()  
      m_myClass.MyInitializationMethod(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 Weitere Informationen über das Hinzufügen eines Assemblyverweises und eines Instanznamens für die benutzerdefinierte Klasse finden Sie unter [Hinzufügen eines Assemblyverweises zu einem Bericht (SSRS)](../report-design/add-an-assembly-reference-to-a-report-ssrs.md).  
  
 Weitere Informationen zur Verwendung der globalen Objektauflistungen finden Sie unter [Integrierte Auflistungen in Ausdrücken (Berichts-Generator und SSRS)](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden benutzerdefinierter Assemblys mit Berichten](using-custom-assemblies-with-reports.md)  
  
  
