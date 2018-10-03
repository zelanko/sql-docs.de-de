---
title: Transparente Netzwerk-IP-Adressauflösung mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d255208f-d486-4ad3-8080-61c6e0261825
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 767e3e17b67a36bca93bd8a85704d50338fdfd58
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610742"
---
# <a name="using-transparent-network-ip-resolution"></a>Verwenden der transparenten Netzwerk-IP-Adressauflösung
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

TransparentNetworkIPResolution ist eine Überarbeitung der vorhandenen MultiSubnetFailover-Funktion, die in Microsoft ODBC Driver 13.1 für SQL Server, die der Verbindungssequenz des Treibers im Fall wirkt sich auf, in dem die erste aufgelöste IP-Adresse des Hostnamens nicht, verfügbar reagieren, und es gibt mehrere IP-Adressen, die den Hostnamen zugeordnet. Er interagiert mit MultiSubnetFailover, um die folgenden drei Verbindungstypen Sequenzen bereitzustellen:

* 0: eine IP versucht wird, gefolgt von allen IP-Adressen parallel
* 1: alle IP-Adressen parallel versucht werden
* 2: alle IP-Adressen versucht werden nacheinander

|TransparentNetworkIPResolution|MultiSubnetFailover|Verhalten|
|:-:|:-:|:-:|
|(Standard)|(Standard)|0|
|(Standard)|Aktiviert|1|
|(Standard)|Disabled|0|
|Aktiviert|(Standard)|0|
|Aktiviert|Aktiviert|1|
|Aktiviert|Disabled|0|
|Disabled|(Standard)|2|
|Disabled|Aktiviert|1|
|Disabled|Disabled|2|

Die `TransparentNetworkIPResolution` Verbindungszeichenfolge und dem DSN-Schlüsselwort steuert diese Einstellung auf der Ebene der Verbindungszeichenfolge. Der Standardwert ist aktiviert.

Schlüsselwort|Werte|Default
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

Die `SQL_COPT_SS_TNIR` vorverbindungsattribut ermöglicht einer Anwendung aus, um diese Einstellung programmgesteuert zu steuern:

Verbindungsattribut|   Instanzgröße bzw.-Typ|  Default| value| und Beschreibung
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER` oder `SQL_IS_UINTEGER`| `SQL_IS_ON`(1), `SQL_IS_OFF`(0)|`SQL_IS_ON`|Aktiviert oder deaktiviert die TNIR.

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recoveryconnectodbclinux-macodbc-driver-on-linux-support-for-high-availability-disaster-recoverymd"></a>Weitere Informationen zu MultiSubnetFailover, finden Sie unter [ODBC-Treiber unter Linux und MacOS – hohe Verfügbarkeit und Notfallwiederherstellung](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
--------------------------------------------------
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
* [Microsoft ODBC Driver for SQL Server unter Windows](../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [SQL Server-Multisubnetzclustering (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)
