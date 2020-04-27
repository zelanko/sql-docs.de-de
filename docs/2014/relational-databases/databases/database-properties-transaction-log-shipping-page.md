---
title: Datenbankeigenschaften (Seite Protokollversand) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.f1
ms.assetid: 72c4e539-fe11-4d57-b977-65b418d5916f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 83ac357d01b616a0010b9c2132f77bbcf89b479b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62917001"
---
# <a name="database-properties-transaction-log-shipping-page"></a>Datenbankeigenschaften (Seite Protokollversand)
  Mithilfe dieser Seite können Sie die Eigenschaften des Protokollversands einer Datenbank konfigurieren und ändern.  
  
 Eine Erläuterung zu den Konzepten des Protokollversands finden Sie unter [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
## <a name="options"></a>Tastatur  
 **Diese Datenbank als primäre Datenbank in einer Protokollversandkonfiguration aktivieren**  
 Aktiviert diese Datenbank als primäre Datenbank im Protokollversand. Aktivieren Sie dieses Kontrollkästchen, und konfigurieren Sie anschließend die übrigen Optionen auf dieser Seite. Wenn Sie dieses Kontrollkästchen deaktivieren, wird die Protokollversandkonfiguration für diese Datenbank aufgehoben.  
  
 **Sicherungseinstellungen**  
 Klicken Sie auf **Sicherungseinstellungen** , um die Parameter für Sicherungszeitplan, Speicherort, Warnung und Archivierung zu konfigurieren.  
  
 **Sicherungszeitplan**  
 Zeigt den zurzeit ausgewählten Sicherungszeitplan der primären Datenbank an. Zum Ändern dieser Einstellungen klicken Sie auf **Sicherungseinstellungen** .  
  
 **Letzte erstellte Sicherung**  
 Zeigt Uhrzeit und Datum der letzten Transaktionsprotokollsicherung an, die für die primäre Datenbank vorgenommen wurde.  
  
 **Sekundäre Serverinstanzen und Datenbanken**  
 Führt die für die primäre Datenbank zurzeit konfigurierten sekundären Serverinstanzen und Datenbanken auf. Markieren Sie eine Datenbank, und klicken Sie dann auf **...** , um Änderungen an den für diese sekundäre Datenbank verfügbaren Parametern vorzunehmen.  
  
 **Add (Hinzufügen)**  
 Klicken Sie auf **Hinzufügen** , um der Protokollversandkonfiguration der primären Datenbank eine sekundäre Datenbank hinzuzufügen.  
  
 **Remove**  
 Entfernt eine ausgewählte Datenbank aus dieser Protokollversandkonfiguration. Wählen Sie zuerst die Datenbank aus, und klicken Sie dann auf **Entfernen**.  
  
 **Überwachungsserverinstanz verwenden**  
 Richtet eine Überwachungsserverinstanz für die Protokollversandkonfiguration ein. Aktivieren Sie das Kontrollkästchen **Überwachungsserverinstanz verwenden** , und klicken Sie dann auf **Einstellungen** , um die Überwachungsserverinstanz anzugeben.  
  
 **Überwachungsserverinstanz**  
 Zeigt die für die Protokollversandkonfiguration zurzeit konfigurierte Überwachungsserverinstanz an.  
  
 **Einstellungen**  
 Konfiguriert die Überwachungsserverinstanz für eine Protokollversandkonfiguration. Klicken Sie auf **Einstellungen** , um die Überwachungsserverinstanz zu konfigurieren.  
  
 **Skript für Konfiguration erstellen**  
 Generiert ein Skript, das den Protokollversand mit den ausgewählten Parametern konfiguriert. Klicken Sie auf **Skript für Konfiguration erstellen**, und wählen Sie dann ein Ausgabeziel für das Skript aus.  
  
> [!IMPORTANT]  
>  Bevor Sie ein Skript für die Einstellungen einer sekundären Datenbank erstellen, müssen Sie das Dialogfeld **Einstellungen für die sekundäre Datenbank** aufrufen. Durch das Aufrufen dieses Dialogfelds wird eine Verbindung mit dem sekundären Server hergestellt, und die aktuellen Eigenschaften der sekundären Datenbank, die zum Generieren des Skripts erforderlich sind, werden abgerufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für den Protokollversand &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql)   
 [Protokollversandtabellen &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-tables-transact-sql)  
  
  
