---
title: Arbeiten mit Datenbankobjekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- database objects [SMO]
- objects [SMO]
ms.assetid: 702fd63d-8734-4a02-872e-aecfb037c787
author: stevestein
ms.author: sstein
ms.openlocfilehash: 14dd0c0175a23f809fc925c5104ac15ac408805b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84996928"
---
# <a name="working-with-database-objects"></a>Arbeiten mit Datenbankobjekten
  Die Phasen der SMO-Objekterstellung sind:  
  
1.  Erstellen einer Instanz des Objekts  
  
2.  Festlegen der Objekteigenschaften  
  
3.  Erstellen von Instanzen der untergeordneten Objekte  
  
4.  Festlegen der Eigenschaften des untergeordneten Objekts  
  
5.  Erstellen des Objekts  
  
 Wenn Instanzen von SMO-Objekten in einer SMO-Anwendung erstellt werden, sind sie auf der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz erst vorhanden, wenn die `Create`-Methode ausgegeben wird. Allerdings ist es nicht notwendig, eine `Create`-Methode für jedes einzelne Objekt auszugeben. Wenn ein Objekt über einen Satz untergeordneter Objekte verfügt, muss nur das übergeordnete Objekt die `Create`-Methode ausführen. Zum Beispiel erfordert die Definition einer Tabelle, dass mindestens eine Spalte darin enthalten ist. Auch kann eine Spalte nicht ohne eine Tabelle erstellt werden. Es besteht eine Abhängigkeitsbeziehung zwischen der Tabelle und ihren Spalten.  
  
 Die <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A>-Methode ermöglicht es Ihnen, Änderungen an einem Objekt vorzunehmen. Mehrere Änderungen an einem Objekt, wie beispielsweise das Hinzufügen untergeordneter Objekte zu einer der Auflistungen des Objekts oder das Ändern eines Eigenschaftswerts, werden zu einem Batch zusammengefasst und in einem Durchgang ausgeführt. Die `Alter`-Methode reduziert den Netzwerkdatenverkehr und verbessert die Gesamtleistung.  
  
 Die `Drop`-Anweisung wird dazu verwendet, ein Objekt und alle seine abhängigen untergeordneten Objekte zu entfernen, die anfänglich zur Objekterstellung erforderlich waren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SMO-Objektmodell](../smo-object-model.md)  
  
  
