---
title: Minimieren der Speicherplatz Verwendung von Protokolldateien | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- log file space in RDS [ADO]
ms.assetid: 669662a0-e20f-483e-ab28-53f66c524c98
author: rothja
ms.author: jroth
ms.openlocfilehash: 1eca3db07301ca45c898f21f558339e5f2ab93e1
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747877"
---
# <a name="minimizing-log-file-space-usage"></a>Minimieren des Verbrauchs an Protokolldatei-Speicherplatz
Eine Protokolldatei wird möglicherweise schnell gefüllt (wodurch der Server angehalten wird), wenn eine große Menge an Aktivität für eine SQL Server Datenbank vorhanden ist. Sie können festlegen, dass die Protokolldatei an einem Prüfpunkt **abgeschnitten** wird, um die Lebensdauer der Protokolldatei für eine Datenbank erheblich zu verlängern.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-65"></a>So aktivieren Sie das Abschneiden für einen Prüfpunkt in Microsoft SQL Server 6,5  
  
1.  Starten Sie Microsoft SQL Server Enterprise-Manager, öffnen Sie die Struktur für den Server, und öffnen Sie dann die Struktur der Daten Bank Geräte.  
  
2.  Doppelklicken Sie auf den Namen der Datenbank, für die dieses Feature aktiviert wird.  
  
3.  Wählen Sie auf der Registerkarte **Datenbank** die Option **Abschneiden**aus.  
  
4.  Wählen Sie auf der Registerkarte **Optionen die Option** **Protokoll bei**Prüfpunkt abschneiden aus, und klicken Sie dann auf **OK**.  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-70"></a>So aktivieren Sie das Abschneiden für einen Prüfpunkt in Microsoft SQL Server 7,0  
  
1.  Starten Sie Microsoft SQL Server Enterprise-Manager, öffnen Sie die Struktur für den Server, und öffnen Sie dann die Struktur der Datenbanken.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Namen der Datenbank, für die dieses Feature aktiviert werden soll, und wählen Sie **Eigenschaften**aus.  
  
3.  Wählen Sie auf der Registerkarte **Optionen die Option** **Protokoll bei**Prüfpunkt abschneiden aus, und klicken Sie dann auf **OK**.  
  
 Weitere Informationen zum Feature " **TRUNCATE on Checkpoint** " finden Sie in der Microsoft SQL Server-Dokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


