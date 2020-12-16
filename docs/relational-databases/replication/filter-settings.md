---
description: Filtereinstellungen
title: Filtereinstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: f6b00d51fab28b9d4b4c66e8deff0194e01e8d41
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97464751"
---
# <a name="filter-settings"></a>Filtereinstellungen
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Im Dialogfeld **Filtereinstellungen** können Sie Filter für Raster im Replikationsmonitor definieren. Wenn Sie z. B. nur die aktiven Abonnements auf der Registerkarte **Alle Abonnements** anzeigen möchten, wählen Sie in der Spalte **Spaltenname** den Eintrag **Status** , in der Spalte **Operator** den Eintrag **Ist gleich** und in der Spalte **Wert1** den Eintrag **Aktiv** aus. Wenn Sie einen auf einer oder mehreren Spalten basierenden Filter definiert haben, wird dieser Filter angewendet, sodass im Raster nur die Teilmenge von Zeilen angezeigt wird, die die Filterkriterien erfüllen.  
  
## <a name="options"></a>Optionen  
 **Spaltenname**  
 Wählen Sie den Namen der Spalte aus, für die Sie einen Filter definieren möchten. Sie können einen Filter für eine oder mehrere Spalten definieren.  
  
 **Operator**  
 Wählen Sie für den Filter einen Operator wie **Kleiner als oder gleich** aus.  
  
 **Wert1** und **Wert2**  
 Geben Sie einen Wert für den Filter ein, oder wählen Sie einen Wert aus. Für die meisten Operatoren muss nur in der Spalte **Wert1** ein Wert eingegeben werden. Für die Operatoren **Zwischen** und **Nicht zwischen** muss jedoch auch in der Spalte **Wert2** ein Wert eingegeben werden.  
  
 **Filter löschen**  
 Klicken Sie auf diese Schaltfläche, um alle definierten Filter zu löschen. Wenn Sie einen einzelnen Filter entfernen möchten, wählen Sie die Filterzeile aus, und drücken Sie die ENTF-TASTE.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Replikation](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
