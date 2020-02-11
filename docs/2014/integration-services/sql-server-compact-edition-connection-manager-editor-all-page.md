---
title: Verbindungs-Manager-Editor für SQL Server Compact Edition (Seite "alle") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlmobileconnection.all.f1
helpviewer_keywords:
- SQL Server Compact Connection Manager Editor
ms.assetid: f9fbff4b-c502-44b3-8e7b-398d66e82206
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8a26587f9dd426cdf53a3a53a36d0e81e95ebf77
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055468"
---
# <a name="sql-server-compact-edition-connection-manager-editor-all-page"></a>Verbindungs-Manager-Editor für SQL Server Compact Edition (Seite Alle)
  Mithilfe des Dialogfelds **Verbindungs-Manager-Editor für SQL Server Compact Edition** können Sie Eigenschaften für die Verbindung mit einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank angeben.  
  
 Weitere Informationen zum [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition-Verbindungs-Manager finden Sie unter [Verbindungs-Manager-Editor für SQL Server Compact Edition](connection-manager/sql-server-compact-edition-connection-manager.md).  
  
## <a name="options"></a>Tastatur  
 **Schwellenwert für automatische Verkleinerung**  
 Gibt den freien Speicherplatz in Prozent an, der in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank zulässig ist, bevor der Prozess des automatischen Verkleinerns ausgeführt wird.  
  
 **Standardmäßige Sperrenausweitung**  
 Gibt die Anzahl der Datenbanksperren an, die die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank abruft, bevor sie versucht, die Sperren auszuweiten.  
  
 **Standard-Sperr Timeout**  
 Gibt das Standardintervall in Millisekunden an, das eine Transaktion auf eine Sperre wartet.  
  
 **Leerungs Intervall**  
 Gibt das Intervall zwischen Transaktionen an, für die ein Commit erfolgt ist, und in dem die Daten auf einen Datenträger gespeichert werden. Zeiteinheit sind Sekunden.  
  
 **Gebiets Schema Bezeichner**  
 Gibt die Gebietsschema-ID (Locale ID, LCID) der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank an.  
  
 **Maximale Puffergröße**  
 Gibt die maximale Menge an Arbeitsspeicher in Kilobyte an, die von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact verwendet werden, bevor die Daten auf einem Datenträger gespeichert werden.  
  
 **Maximale Datenbankgröße**  
 Gibt die Maximalgröße der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank in Megabyte an.  
  
 **Mode**  
 Gibt an, in welchem Dateimodus die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank zu öffnen ist. Der Standardwert für diese Eigenschaft lautet **Read Write**.  
  
 Die Option Mode kann vier Werte annehmen. Siehe dazu die folgende Tabelle.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Nur Leseberechtigung**|Gibt an, dass der Zugriff auf die Datenbank schreibgeschützt erfolgen kann.|  
|**Lesen Schreiben**|Gibt Lese-/Schreibberechtigungen für die Datenbank an.|  
|**Exklusiv**|Gibt exklusiven Zugriff auf die Datenbank an.|  
|**Gemeinsamer Lesevorgang**|Gibt an, dass andere Benutzer zu selben Zeit Daten aus der Datenbank lesen können.|  
  
 **Persistente Sicherheitsinformationen**  
 Gibt an, ob als Teil der Verbindungszeichenfolge Sicherheitsinformationen zurückgegeben werden sollen. Der Standardwert für diese Option ist **False**.  
  
 **Temporäres Datei Verzeichnis**  
 Geben Sie den Pfad der temporären [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbankdatei an.  
  
 **Data Source**  
 Geben Sie den Namen der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank an.  
  
 **Kennwort**  
 Geben Sie das Kennwort für die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [SQL Server Compact Editions Verbindungs-Manager-Editor &#40;Seite "Verbindung"&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
  
