---
title: Objektabhängigkeiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.objectdependencies.f1
ms.assetid: c63d1160-3f3d-45df-99be-6fe081125fb5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bba5156d159c87ad6ad0e011268bc655b45a5c37
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63032417"
---
# <a name="object-dependencies"></a>Objektabhängigkeiten
  Bestimmte Datenbankobjekte sind von anderen Datenbankobjekten abhängig. Sichten und gespeicherte Prozeduren sind beispielsweise vom Vorhandensein von Tabellen abhängig, die die von der Sicht oder der Prozedur zurückgegebenen Daten enthalten. Auf der Seite „Allgemein“ des Dialogfelds **Objektabhängigkeiten** für das aktuelle Objekt sind sowohl die Datenbankobjekte aufgeführt, die für die ordnungsgemäße Funktion des Objekts vorhanden sein müssen, als auch die Objekte, die vom ausgewählten Objekt abhängig sind. Ein Objekt, das in seiner im Systemkatalog gespeicherten Definition auf ein anderes Objekt verweist, wird als *verweisende Entität*bezeichnet. Ein Objekt, auf das von einem anderen Objekt verwiesen wird, wird als *Entität, auf die verwiesen wird*bezeichnet.  
  
 Unter **Objektabhängigkeiten** (erweiterte Seite) für die aktuellen Objekte werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankobjekte und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Objekte aufgeführt, die vom aktuellen Objekt abhängen. Die Objekte werden möglicherweise auf verschiedenen Servern gespeichert.  
  
 Mithilfe dieses Dialogfelds können Sie sich einen Überblick über die Abhängigkeiten verschaffen, bevor Sie das ausgewählte Objekt ändern oder löschen.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Objekte, die vom**  _\<ausgewählten Objekt abhängig sind>_  
 Durch Klicken auf diese Schaltfläche wird eine Liste der Objekte angezeigt, deren Abhängigkeiten nachverfolgt werden und die vom ausgewählten Objekt abhängig sind.  
  
 **Objekte, von denen das**_\<ausgewählte Objekt>_ **abhängig** ist      
 Durch Klicken auf diese Schaltfläche wird eine Liste der Objekte angezeigt, deren Abhängigkeiten nachverfolgt werden und von denen das ausgewählte Objekt abhängig ist.  
  
 **Zen**  
 Wenn **auf** _ \<Objekte, die von ausgewähltem Objekt>_ abhängen, geklickt wird, wird eine hierarchische Ansicht der Objekte angezeigt, die vom ausgewählten Objekt abhängig sind. Wenn **auf Objekte, von denen** _ \<das ausgewählte Objekt>_ **abhängt** , geklickt wird, wird eine hierarchische Ansicht der Objekte angezeigt, von denen das ausgewählte Objekt abhängig ist.  
  
 **Name**  
 Zeigt den Namen, des oben in der Strukturansicht **Abhängigkeiten** ausgewählten Objekts an.  
  
 **Typ**  
 Zeigt den Typ des oben in der Strukturansicht **Abhängigkeiten** ausgewählten Objekts an.  
  
 **Zeitpunkt der letzten Synchronisierung**  
 > [!NOTE]  
>  Diese Option ist nur auf der Seite **Erweitert** verfügbar.  
  
 Gibt das Datum und die Uhrzeit des letzten Updates der Abhängigkeitsinformationen an.  
  
 **Abhängigkeits Typen**  
 > [!NOTE]  
>  Diese Option ist nur auf der Seite **Allgemein** verfügbar.  
  
 Zeigt den Typ der Abhängigkeit zwischen zwei Objekten an. Dabei kann es sich um eine der folgenden Methoden handeln:  
  
-   Schemagebundene Abhängigkeit  
  
     Dies ist eine Beziehung zwischen zwei Objekten, mit der verhindert wird, dass das Objekt, auf das verwiesen wird, gelöscht oder geändert wird, solange das verweisende Objekt vorhanden ist. Eine schemagebundene Abhängigkeit wird erstellt, wenn eine Sicht oder eine benutzerdefinierte Funktion mithilfe der WITH SCHEMABINDING-Klausel erstellt wird oder eine Tabelle über eine CHECK- oder DEFAULT-Einschränkung bzw. in der Definition einer berechneten Spalte auf ein anderen Objekt verweist.  
  
-   Nicht schemagebundene Abhängigkeit  
  
     Dies ist eine Beziehung zwischen zwei Objekten, mit der nicht verhindert wird, dass das Objekt, auf das verwiesen wird, gelöscht oder geändert wird.  
  
-   Nicht verfügbare oder nicht aufgelöste Entität  
  
     Gibt an, dass der Abhängigkeitstyp nicht bestimmt werden kann. Dies geschieht nur, wenn sich das ausgewählte Objekt auf einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befindet, bei der es sich um eine frühere Version von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]handelt.  
  
  
