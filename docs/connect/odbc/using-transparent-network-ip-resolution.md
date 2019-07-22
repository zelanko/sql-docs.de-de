---
title: Verwenden der transparenten Netzwerk-IP-Auflösung | Microsoft-Dokumentation
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
ms.openlocfilehash: df5b0233168c52b4f79cdc6d2d03cd7b72e16046
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008484"
---
# <a name="using-transparent-network-ip-resolution"></a>Verwenden der transparenten Netzwerk-IP-Adressauflösung
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

Transparentnetworkipresolution ist eine Revision des vorhandenen multisubnetfailover-Features, das in Microsoft ODBC Driver 13,1 für SQL Server verfügbar ist, das sich auf die Verbindungs Sequenz des Treibers auswirkt, wenn die erste aufgelöste IP-Adresse des Host Namens nicht vorliegt. reagieren Sie, und dem Hostnamen sind mehrere IP-Adressen zugeordnet. Es interagiert mit multisubnetfailover, um die folgenden drei Verbindungs Sequenzen bereitzustellen:

* 0: Es wird versucht, eine IP-Adresse und danach alle IPS parallel auszuführen.
* 1: alle IPS werden parallel versucht
* 2: alle IPS werden nacheinander versucht

|TransparentNetworkIPResolution|MultiSubnetFailover|ESS|
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

Die `TransparentNetworkIPResolution` Verbindungs Zeichenfolge und das DSN-Schlüsselwort steuern diese Einstellung auf der Ebene der Verbindungs Zeichenfolge. Die Standardeinstellung ist aktiviert.

Schlüsselwort|Werte|Default
-|-|-
`TransparentNetworkIPResolution`|`Yes`, `No`|`Yes`

Mit `SQL_COPT_SS_TNIR` dem präconnection-Attribut kann eine Anwendung diese Einstellung Programm gesteuert Steuern:

Verbindungsattribut|   Größe/Typ|  Default| value| und Beschreibung
-|-|-|-|-
`SQL_COPT_SS_TNIR` (1249)| `SQL_IS_INTEGER` oder `SQL_IS_UINTEGER`| `SQL_IS_ON`(1), `SQL_IS_OFF`(0)|`SQL_IS_ON`|Aktiviert oder deaktiviert tnir.

<a name="for-more-information-about-multisubnetfailover-see-odbc-driver-on-linux-and-macos---high-availability-and-disaster-recoveryconnectodbclinux-macodbc-driver-on-linux-support-for-high-availability-disaster-recoverymd"></a>Weitere Informationen zu multisubnetfailover finden Sie unter [ODBC-Treiber unter Linux und macOS-hohe Verfügbarkeit und Notfall Wiederherstellung](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md) .
--------------------------------------------------
## <a name="see-also"></a>Weitere Informationen  
* [Microsoft ODBC Driver for SQL Server unter Windows](../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
* [SQL Server-Multisubnetzclustering (SQL Server)](https://msdn.microsoft.com/library/ff878716.aspx#RelatedContent)
