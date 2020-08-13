---
title: Arbeiten mit Resultsets
description: Hier erfahren Sie, wie Sie in diesen Beispielanwendungen Daten mithilfe von Resultsets im JDBC-Treiber für SQL Server bearbeiten.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4fc4b1c6-3075-4ad7-9244-865d9ede7ae6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 82618ee27e1aa32716fe4b4d3817ff0128baebab
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921026"
---
# <a name="working-with-result-sets"></a>Arbeiten mit Resultsets

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Bei der Verarbeitung von Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank besteht eine Methode zum Bearbeiten der Daten darin, ein Resultset zu verwenden. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unterstützt die Verwendung von Resultsets über das [SQLServerResultSet](reference/sqlserverresultset-class.md)-Objekt. Mithilfe des SQLServerResultSet-Objekts können Sie die von einer SQL-Anweisung oder gespeicherten Prozedur zurückgegebenen Daten abrufen, die Daten bei Bedarf aktualisieren und dann wieder in der Datenbank speichern.

Das SQLServerResultSet-Objekt enthält darüber hinaus Methoden, um in den Datenzeilen zu navigieren, die enthaltenen Daten abzurufen oder festzulegen und die Sensitivität gegenüber Änderungen in der zugrunde liegenden Datenbank einzurichten.

> [!NOTE]
> Weitere Informationen zur Verwaltung von Resultsets, einschließlich deren Empfindlichkeit gegenüber Änderungen, finden Sie unter [Verwalten von Resultsets mit dem JDBC-Treiber](managing-result-sets-with-the-jdbc-driver.md).

Die Themen in diesem Abschnitt beschreiben verschiedene Möglichkeiten, wie Sie die in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank enthaltenen Daten mithilfe von Resultsets bearbeiten können.

## <a name="in-this-section"></a>In diesem Abschnitt

| Thema                                                                     | BESCHREIBUNG                                                                                                                                                                                          |
| ------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Abrufen von Resultsetdaten – Beispiel](retrieving-result-set-data-sample.md) | Beschreibt die Verwendung eines Resultsets, um Daten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank abzurufen und anzuzeigen.                                                         |
| [Ändern von Resultsetdaten – Beispiel](modifying-result-set-data-sample.md)   | Beschreibt die Verwendung eines Resultsets, um Daten in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank einzufügen, daraus abzurufen bzw. darin zu ändern.                                                      |
| [Zwischenspeichern von Resultsetdaten – Beispiel](caching-result-set-data-sample.md)       | Beschreibt die Verwendung eines Resultsets, um umfangreiche Daten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank abzurufen, sowie die Steuerung der Zwischenspeicherung dieser Daten im Client. |

## <a name="see-also"></a>Weitere Informationen

[Beispiele für JDBC-Treiberanwendungen](sample-jdbc-driver-applications.md)
