---
title: Objektabhängigkeiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.common.objectdependencies.f1
ms.assetid: c63d1160-3f3d-45df-99be-6fe081125fb5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d78edce14b7e88648ce134c2bb3d7def7003f516
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65102982"
---
# <a name="object-dependencies"></a>Objektabhängigkeiten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Bestimmte Datenbankobjekte sind von anderen Datenbankobjekten abhängig. Sichten und gespeicherte Prozeduren sind beispielsweise vom Vorhandensein von Tabellen abhängig, die die von der Sicht oder der Prozedur zurückgegebenen Daten enthalten. Auf der Seite „Allgemein“ des Dialogfelds **Objektabhängigkeiten** für das aktuelle Objekt sind sowohl die Datenbankobjekte aufgeführt, die für die ordnungsgemäße Funktion des Objekts vorhanden sein müssen, als auch die Objekte, die vom ausgewählten Objekt abhängig sind. Ein Objekt, das in seiner im Systemkatalog gespeicherten Definition auf ein anderes Objekt verweist, wird als *verweisende Entität*bezeichnet. Ein Objekt, auf das von einem anderen Objekt verwiesen wird, wird als *Entität, auf die verwiesen wird*bezeichnet.  
  
Unter **Objektabhängigkeiten** (erweiterte Seite) für die aktuellen Objekte werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankobjekte und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Objekte aufgeführt, die vom aktuellen Objekt abhängen. Die Objekte werden möglicherweise auf verschiedenen Servern gespeichert.  
  
Mithilfe dieses Dialogfelds können Sie sich einen Überblick über die Abhängigkeiten verschaffen, bevor Sie das ausgewählte Objekt ändern oder löschen.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
**Objekte, die von** _\<ausgewähltes Objekt>_ abhängig sind  
Durch Klicken auf diese Schaltfläche wird eine Liste der Objekte angezeigt, deren Abhängigkeiten nachverfolgt werden und die vom ausgewählten Objekt abhängig sind.  
  
**Objekte, von denen** _\<ausgewähltes Objekt>_ **abhängt**  
Durch Klicken auf diese Schaltfläche wird eine Liste der Objekte angezeigt, deren Abhängigkeiten nachverfolgt werden und von denen das ausgewählte Objekt abhängig ist.  
  
**Abhängigkeiten**  
Nach dem Klicken auf **Objekte, die von** *<selected object>* abhängig sind, wird eine hierarchische Ansicht der Objekte angezeigt, die von dem ausgewählten Objekt abhängig sind. Durch Klicken auf **Objekte, von denen** *<selected object>* **abhängt**, wird eine hierarchische Ansicht von Objekten angezeigt, von denen das ausgewählte Objekt abhängig ist.  
  
**Name**  
Zeigt den Namen, des oben in der Strukturansicht **Abhängigkeiten** ausgewählten Objekts an.  
  
**Typ**  
Zeigt den Typ des oben in der Strukturansicht **Abhängigkeiten** ausgewählten Objekts an.  
  
**Zeit der letzten Synchronisierung**  
> [!NOTE]  
> Diese Option ist nur auf der Seite **Erweitert** verfügbar.  
  
Gibt das Datum und die Uhrzeit des letzten Updates der Abhängigkeitsinformationen an.  
  
**Abhängigkeitstyp**  
> [!NOTE]  
> Diese Option ist nur auf der Seite **Allgemein** verfügbar.  
  
Zeigt den Typ der Abhängigkeit zwischen zwei Objekten an. Kann einen der folgenden Werte annehmen:  
  
-   Schemagebundene Abhängigkeit  
  
    Dies ist eine Beziehung zwischen zwei Objekten, mit der verhindert wird, dass das Objekt, auf das verwiesen wird, gelöscht oder geändert wird, solange das verweisende Objekt vorhanden ist. Eine schemagebundene Abhängigkeit wird erstellt, wenn eine Sicht oder eine benutzerdefinierte Funktion mithilfe der WITH SCHEMABINDING-Klausel erstellt wird oder eine Tabelle über eine CHECK- oder DEFAULT-Einschränkung bzw. in der Definition einer berechneten Spalte auf ein anderen Objekt verweist.  
  
-   Nicht schemagebundene Abhängigkeit  
  
    Dies ist eine Beziehung zwischen zwei Objekten, mit der nicht verhindert wird, dass das Objekt, auf das verwiesen wird, gelöscht oder geändert wird.  
  
-   Nicht verfügbare oder nicht aufgelöste Entität  
  
    Gibt an, dass der Abhängigkeitstyp nicht bestimmt werden kann. Dies geschieht nur, wenn sich das ausgewählte Objekt auf einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befindet, bei der es sich um eine frühere Version von [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)]handelt.  
  
