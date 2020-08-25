---
title: Konfigurieren der polybase-Konnektivität
description: Erläutert das parallele Konfigurieren von polybase Data Warehouse zum Herstellen einer Verbindung mit externen Hadoop-oder Microsoft Azure Storage-BLOB-Datenquellen. Verwenden Sie polybase zum Ausführen von Abfragen, die Daten aus mehreren Quellen integrieren, einschließlich Hadoop, Azure BLOB Storage und parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 98527bf770da61c98368171e75b3a9b82ceba13c
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88767179"
---
# <a name="configure-polybase-connectivity"></a>Konfigurieren der polybase-Konnektivität
Polybase ermöglicht Ihrem Analytics Platform System (APS) die Verarbeitung von Transact-SQL-Abfragen, die Daten aus externen Datenquellen lesen und in diese schreiben können. Die gleichen Abfragen, die auf externe Daten zugreifen, können auch Beziehungs Tabellen in ihren APS enthalten. Auf diese Weise können Sie Daten aus externen Quellen mit wichtigen relationalen Daten in ihren APS-Datenbanken kombinieren.

![PolyBase-Logik](media/polybase/polybase-logical.png)

Polybase on APS unterstützt das Lesen und Schreiben in das HDFS-Dateisystem (Hadoop) und Azure BLOB Storage. Polybase ist auch in der Lage, einige Berechnungen als MapReduce-Aufträge an Hadoop-Knoten zu überbringen, um die gesamte Abfrageleistung zu optimieren. Polybase in APS kann mit durch Trennzeichen getrennten Text-, Orc-und Parkett Dateien betrieben werden. Eine vollständige Beschreibung und deren Funktionen finden Sie unter [Was ist polybase](../relational-databases/polybase/polybase-guide.md) ?.

> [!NOTE]
> APS unterstützt zurzeit nur standardmäßig lokal redundante Standard-Azure BLOB Storage (LRS).

## <a name="features-and-limitations"></a>Features und Einschränkungen
Unter [Features und Einschränkungen](../relational-databases/polybase/polybase-versioned-feature-summary.md) finden Sie eine Übersicht über die verfügbaren polybase-Features und bekannte Einschränkungen für APS und andere SQL Server Produkte.

> [!NOTE] 
> In den restlichen polybase-Artikeln wird beschrieben, wie polybase auf APS 2016 (AU6) und höher konfiguriert wird.

## <a name="see-also"></a>Weitere Informationen
- [Hadoop](polybase-configure-hadoop.md)
- [Azure Blob Storage](polybase-configure-azure-blob-storage.md)
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
