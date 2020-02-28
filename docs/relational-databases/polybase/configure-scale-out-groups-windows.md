---
title: Konfigurieren von PolyBase-Erweiterungsgruppen unter Windows | Microsoft-Dokumentation
ms.date: 04/23/2019
ms.prod: sql
ms.technology: polybase
ms.topic: tutorial
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: ''
monikerRange: '>= sql-server-2016 || =sqlallproducts-allversions'
ms.openlocfilehash: dfc8560c9834d920a132a54587ba80947db9425d
ms.sourcegitcommit: 49082f9b6b3bc8aaf9ea3f8557f40c9f1b6f3b0b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2020
ms.locfileid: "77256753"
---
# <a name="configure-polybase-scale-out-groups-on-windows"></a>Konfigurieren von PolyBase-Erweiterungsgruppen unter Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird beschrieben, wie Sie eine [PolyBase-Erweiterungsgruppe](polybase-scale-out-groups.md) unter Windows einrichten. Mit diesem Verfahren wird ein Cluster aus SQL Server-Instanzen erstellt, der durch horizontale Skalierung für bessere Abfrageleistungen bei großen Datasets aus externen Datenquellen sorgt, wie beispielsweise Hadoop oder Azure Blob Storage.

## <a name="prerequisites"></a>Voraussetzungen
  
- Mehr als ein Computer in der gleichen Domäne  
  
- Ein Domänenbenutzerkonto zum Ausführen von PolyBase-Diensten  
  
## <a name="process-overview"></a>Übersicht über den Prozess

Die folgenden Schritte fassen den Prozess der Erstellung einer PolyBase-Erweiterungsgruppe zusammen. Im nächsten Abschnitt finden Sie eine ausführliche exemplarische Vorgehensweise für jeden Schritt.
  
1. Installieren Sie die gleiche Version von SQL Server mit PolyBase auf N Computern.
  
2. Wählen Sie eine SQL Server-Instanz als Hauptknoten aus. Ein Hauptknoten kann nur auf einer Instanz festgelegt werden, die SQL Server Enterprise ausführt.
  
3. Fügen Sie mithilfe von [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md)die verbleibenden SQL Server-Instanzen als Serverknoten hinzu.

4. Überwachen Sie Knoten in der Gruppe mit [sys.dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).

5. Optional. Entfernen Sie einen Serverknoten mit [sp_polybase_leave_group &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-leave-group.md).

## <a name="example-walk-through"></a>Exemplarische Vorgehensweise

Hier erfahren Sie, wie Sie eine PolyBase-Gruppe mit den folgenden Informationen einrichten:  
  
1. Zwei Computer in der Domäne *PQTH4A* Die Namen der Computer sind:  
  
   - PQTH4A-CMP01  
  
   - PQTH4A-CMP02  
  
2. Domänenkonto: *PQTH4A\PolyBaseUse*r  

## <a name="install-sql-server-with-polybase-on-all-machines"></a>Installieren von SQL Server mit PolyBase auf allen Computern

1. Führen Sie „setup.exe“ aus.
  
2. Wählen Sie auf der Seite „Funktionsauswahl“ **PolyBase Query Service for External Data** (PolyBase-Abfragedienst für externe Daten).
  
3. Verwenden Sie das **Domänenkonto** „PQTH4A\PolyBaseUser“ für die SQL Server-PolyBase-Engine und den SQL Server PolyBase-Datenverschiebungsdienst auf der Konfigurationsseite des Servers.
  
4. Wählen Sie auf der PolyBase-Konfigurationsseite die Option **Use the SQL Server instance as part of a PolyBase scale-out group**(SQL Server-Instanz als Teil einer PolyBase-Erweiterungsgruppe verwenden). Dies öffnet die Firewall, um eingehende Verbindungen an die PolyBase-Dienste zuzulassen. Wenn der Hauptknoten eine benannte Instanz ist, müssen Sie den SQL Server-Port manuell zur Windows-Firewall auf dem Hauptknoten hinzufügen und den SQL-Browser auf dem Hauptknoten starten.
  
5. Nachdem das Setup abgeschlossen ist, führen Sie **services.msc**aus. Überprüfen Sie, ob SQL Server, die PolyBase-Engine und der PolyBase-Datenverschiebungsdienst ausgeführt werden.
  
   ![PolyBase-Dienste](../../relational-databases/polybase/media/polybase-services.png "PolyBase-Dienste")  
  
## <a name="select-one-sql-server-as-head-node"></a>Auswählen einer SQL Server-Instanz als Hauptknoten  
  
Nachdem das Setup abgeschlossen ist, können beide Computer als PolyBase-Gruppenhauptknoten fungieren. In diesem Beispiel wählen wir MSSQLSERVER auf PQTH4A-CMP01 als den Hauptknoten.
  
## <a name="add-other-sql-server-instances-as-compute-nodes"></a>Hinzufügen weiterer SQL Server-Instanzen als Computeknoten  
  
1. Stellen Sie die Verbindung mit SQL Server auf PQTH4A-CMP02 her.
  
2. Führen Sie die gespeicherte Prozedur [sp_polybase_leave_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md)aus.

   ```sql
   -- Enter head node details:
   -- head node machine name, head node dms control channel port, head node sql server name  
    EXEC sp_polybase_join_group 'PQTH4A-CMP01', 16450, 'MSSQLSERVER';
   ```  

3. Führen Sie „services.msc“ auf den Computeknoten (PQTH4A CMP02) aus.
  
4. Fahren Sie die PolyBase-Engine herunter, und starten Sie den PolyBase-Datenverschiebedienst neu.
  
## <a name="optional-remove-a-compute-node"></a>Optional: Entfernen eines Serverknotens  
  
1. Stellen Sie eine Verbindung mit dem Computeknoten SQL Server (PQTH4A-CMP02) her.
  
2. Führen Sie die gespeicherte Prozedur „sp_polybase_leave_group“ aus.
  
    ```sql  
    EXEC sp_polybase_leave_group;  
    ```  
  
3. Führen Sie „services.msc“ auf dem Computeknoten (PQTH4A CMP02) aus, der entfernt wird.
  
4. Starten Sie die PolyBase-Engine. Starten Sie den SQL Server PolyBase-Datenverschiebungsdienst neu.
  
5. Überprüfen Sie, ob der Knoten entfernt wurde, indem Sie die DMV „sys.dm_exec_compute_nodes“ auf PQTH4A CMP01 ausführen. Jetzt fungiert PQTH4A-CMP02 als eigenständiger Hauptknoten.  
  
## <a name="next-steps"></a>Nächste Schritte  

Informationen zur Problembehandlung finden Sie unter [PolyBase troubleshooting with dynamic management views](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80).
  
Weitere Informationen zu PolyBase finden Sie im [PolyBase-Leitfaden](../../relational-databases/polybase/polybase-guide.md).
