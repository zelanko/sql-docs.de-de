---
title: Für SQLServer Compact Edition-Verbindungs-Manager-Editor (Seite "alle") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlmobileconnection.all.f1
helpviewer_keywords:
- SQL Server Compact Connection Manager Editor
ms.assetid: f9fbff4b-c502-44b3-8e7b-398d66e82206
caps.latest.revision: 25
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1d74007858a1834b4d0aba5538e62824f7cee8c6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192110"
---
# <a name="sql-server-compact-edition-connection-manager-editor-all-page"></a>Verbindungs-Manager-Editor für SQL Server Compact Edition (Seite Alle)
  Mithilfe des Dialogfelds **Verbindungs-Manager-Editor für SQL Server Compact Edition** können Sie Eigenschaften für die Verbindung mit einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank angeben.  
  
 Weitere Informationen zum [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition-Verbindungs-Manager finden Sie unter [Verbindungs-Manager-Editor für SQL Server Compact Edition](connection-manager/sql-server-compact-edition-connection-manager.md).  
  
## <a name="options"></a>Tastatur  
 **AutoShrink Threshold**  
 Gibt den freien Speicherplatz in Prozent an, der in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank zulässig ist, bevor der Prozess des automatischen Verkleinerns ausgeführt wird.  
  
 **Default Lock Escalation**  
 Gibt die Anzahl der Datenbanksperren an, die die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank abruft, bevor sie versucht, die Sperren auszuweiten.  
  
 **Default Lock Timeout**  
 Gibt das Standardintervall in Millisekunden an, das eine Transaktion auf eine Sperre wartet.  
  
 **Flush Interval**  
 Gibt das Intervall zwischen Transaktionen an, für die ein Commit erfolgt ist, und in dem die Daten auf einen Datenträger gespeichert werden. Zeiteinheit sind Sekunden.  
  
 **Locale Identifier**  
 Gibt die Gebietsschema-ID (Locale ID, LCID) der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank an.  
  
 **Max Buffer Size**  
 Gibt die maximale Menge an Arbeitsspeicher in Kilobyte an, die von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact verwendet werden, bevor die Daten auf einem Datenträger gespeichert werden.  
  
 **Max Database Size**  
 Gibt die Maximalgröße der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank in Megabyte an.  
  
 **Mode**  
 Gibt an, in welchem Dateimodus die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank zu öffnen ist. Der Standardwert für diese Eigenschaft lautet **Read Write**.  
  
 Die Option Mode kann vier Werte annehmen. Siehe dazu die folgende Tabelle.  
  
|value|Description|  
|-----------|-----------------|  
|**Schreibgeschützt**|Gibt an, dass der Zugriff auf die Datenbank schreibgeschützt erfolgen kann.|  
|**Read Write**|Gibt Lese-/Schreibberechtigungen für die Datenbank an.|  
|**Exclusive**|Gibt exklusiven Zugriff auf die Datenbank an.|  
|**Shared Read**|Gibt an, dass andere Benutzer zu selben Zeit Daten aus der Datenbank lesen können.|  
  
 **Sicherheitsinformationen permanent speichern**  
 Gibt an, ob als Teil der Verbindungszeichenfolge Sicherheitsinformationen zurückgegeben werden sollen. Der Standardwert für diese Option ist **False**.  
  
 **Temp File Directory**  
 Geben Sie den Pfad der temporären [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbankdatei an.  
  
 **Datenquelle**  
 Geben Sie den Namen der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank an.  
  
 **Kennwort**  
 Geben Sie das Kennwort für die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Datenbank ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Für SQLServer Compact Edition-Verbindungs-Manager-Editor &#40;Seite "Verbindung"&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
  
