---
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: fbf94f1ef3926c43f44e293f783ba0f1ac57fac9
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68767698"
---
# <a name="filter-settings"></a>Filtereinstellungen
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Im Dialogfeld **Filtereinstellungen** können Sie Filter für Raster im Replikationsmonitor definieren. Wenn Sie z. B. nur die aktiven Abonnements auf der Registerkarte **Alle Abonnements** anzeigen möchten, wählen Sie in der Spalte **Spaltenname** den Eintrag **Status** , in der Spalte **Operator** den Eintrag **Ist gleich** und in der Spalte **Wert1** den Eintrag **Aktiv** aus. Wenn Sie einen auf einer oder mehreren Spalten basierenden Filter definiert haben, wird dieser Filter angewendet, sodass im Raster nur die Teilmenge von Zeilen angezeigt wird, die die Filterkriterien erfüllen.  
  
## <a name="options"></a>enthalten  
 **Status**  
 Wählen Sie den Namen der Spalte aus, für die Sie einen Filter definieren möchten. Sie können einen Filter für eine oder mehrere Spalten definieren.  
  
 **Ist gleich**  
 Wählen Sie für den Filter einen Operator wie **Kleiner als oder gleich**aus.  
  
 **Wert1** und **Wert2**  
 Geben Sie einen Wert für den Filter ein, oder wählen Sie einen Wert aus. Für die meisten Operatoren muss nur in der Spalte **Wert1** ein Wert eingegeben werden. Für die Operatoren **Zwischen** und **Nicht zwischen** muss jedoch auch in der Spalte **Wert2** ein Wert eingegeben werden.  
  
 **Filter löschen**  
 Klicken Sie auf diese Schaltfläche, um alle definierten Filter zu löschen. Wenn Sie einen einzelnen Filter entfernen möchten, wählen Sie die Filterzeile aus, und drücken Sie die ENTF-TASTE.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Replikation](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
