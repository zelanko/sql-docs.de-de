---
title: Versionshinweise (OLE DB-Treiber für SQL Server)
ms.date: 02/27/2020
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: genemi
author: mateusz-kmiecik
ms.author: v-makmie
ms.openlocfilehash: 2c50ae262516fab757d4de7c254af79f0184ea84
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "80345436"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Anmerkungen zu dieser Version vom OLE DB-Treiber für SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Auf dieser Seite wird erläutert, was in den einzelnen Versionen des Microsoft OLE DB-Treibers für SQL Server hinzugefügt wurde.

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

## <a name="1830"></a>18.3.0

![Download](../../ssms/media/download-icon.png) [Herunterladen des x64-Installationsprogramms](https://go.microsoft.com/fwlink/?linkid=2117515)  
![Download](../../ssms/media/download-icon.png) [Herunterladen des x86-Installationsprogramms](https://go.microsoft.com/fwlink/?linkid=2117517)  

Veröffentlichung: Oktober 2019

Wenn Sie das Installationsprogramm in einer anderen Sprache als der für Sie erkannten herunterladen möchten, können Sie hierfür einen der folgenden direkten Links verwenden.  
Für den x64-Treiber: [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x40a)  
Für den x86-Treiber: [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x40a)  

### <a name="features-added"></a>Neue Features:

| Neues Feature | Details |
| :------------ | :------ |
| Unterstützung für die Azure Active Directory-Authentifizierung (`ActiveDirectoryInteractive`, `ActiveDirectoryMSI`). | [Verwenden von Azure Active Directory](features/using-azure-active-directory.md). |
| Die Active Directory-Authentifizierungsbibliothek (adal.dll) wurde zum Installer hinzugefügt | Dieses Feature ist nun Teil der Installation des Basistreibers. Das OLE DB-Installationsprogramm sorgt dafür, dass ein Upgrade für bestehende Installationen der Microsoft Active Directory-Authentifizierungsbibliothek für SQL Server durchgeführt und die Bibliothek aus der Liste mit installierten Anwendungen in Windows entfernt wird. |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>Behobene Probleme

| Behobene Fehler | Details |
| :-------- | :------ |
| Probleme mit der DROP INDEX-Logik in [IIndexDefinition::DropIndex](https://go.microsoft.com/fwlink/?linkid=2106448) wurden behoben. | Frühere Versionen des OLE DB-Treibers können keinen Primärschlüsselindex ablegen, wenn die Schema- und die Benutzer-ID des Indexbesitzers nicht gleich sind. |
| &nbsp; | &nbsp; |

## <a name="previous-releases"></a>Vorgängerversionen

Laden Sie frühere Versionen des OLE DB Treibers herunter, indem Sie auf die Downloadlinks in den folgenden Abschnitten klicken:

## <a name="1823"></a>18.2.3.0

![Download](../../ssms/media/download-icon.png) [Herunterladen des x64-Installationsprogramms](https://go.microsoft.com/fwlink/?linkid=2119554)  
![Download](../../ssms/media/download-icon.png) [Herunterladen des x86-Installationsprogramms](https://go.microsoft.com/fwlink/?linkid=2119738)  

Veröffentlichung: Juni 2019

Wenn Sie das Installationsprogramm in einer anderen Sprache als der für Sie erkannten herunterladen möchten, können Sie hierfür einen der folgenden direkten Links verwenden.  
Für den x64-Treiber: [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x40a)  
Für den x86-Treiber: [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x40a)  

### <a name="features-added-in-1823"></a>In 18.2.3 hinzugefügte Features

| Neues Feature | Details |
| :------------ | :------ |
| Unterstützung für Treiberupgrades über SQL Server-Wechselmedien | Durch diese Verbesserungen können Treiberupgrades direkt über SQL Server-Wechselmedien durchgeführt werden. |
| &nbsp; | &nbsp; |

## <a name="1822"></a>18.2.2

![Download](../../ssms/media/download-icon.png) [Herunterladen des x64-Installationsprogramms](https://go.microsoft.com/fwlink/?linkid=2118512)  
![Download](../../ssms/media/download-icon.png) [Herunterladen des x86-Installationsprogramms](https://go.microsoft.com/fwlink/?linkid=2118415)  

Veröffentlichung: Mai 2019

Wenn Sie das Installationsprogramm in einer anderen Sprache als der für Sie erkannten herunterladen möchten, können Sie hierfür einen der folgenden direkten Links verwenden.  
Für den x64-Treiber: [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x40a)  
Für den x86-Treiber: [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x40a)  

### <a name="bugs-fixed-in-1822"></a>In 18.2.2 behobene Fehler

| Behobene Fehler | Details |
| :-------- | :------ |
| Die nicht interaktive Azure Active Directory-Authentifizierung im Multithread-Apartment-Modus (MTA) wurde behoben. | Der OLE DB-Treiber Version 18.2.1 versucht fälschlicherweise das COM-Parallelitätsmodell für ein Apartment zu ändern, das zuvor als Multithread-Apartment (MTA) initialisiert wurde. Daher kann der Treiber in einer Anwendung, die vor dem Aufruf der Schnittstelle [IDBInitialize::Initialize](https://go.microsoft.com/fwlink/?linkid=2092522) mehr als einen nachfolgenden Aufruf von [CoInitialize](https://go.microsoft.com/fwlink/?linkid=2092520) oder [CoInitializeEx](https://go.microsoft.com/fwlink/?linkid=2092521) durchführt, keine Verbindung herstellen, wenn ein Azure Active Directory-Authentifizierungsmodus verwendet wird. |
| &nbsp; | &nbsp; |

## <a name="1821"></a>18.2.1

![Download](../../ssms/media/download-icon.png) [Herunterladen des x64-Installationsprogramms](https://go.microsoft.com/fwlink/?linkid=2118511)  
![Download](../../ssms/media/download-icon.png) [Herunterladen des x86-Installationsprogramms](https://go.microsoft.com/fwlink/?linkid=2118278)  

Veröffentlichung: Februar 2019

Wenn Sie das Installationsprogramm in einer anderen Sprache als der für Sie erkannten herunterladen möchten, können Sie hierfür einen der folgenden direkten Links verwenden.  
Für den x64-Treiber: [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x40a)  
Für den x86-Treiber: [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x40a)  

### <a name="features-added-in-1821"></a>In 18.2.1 hinzugefügte Features

| Neues Feature | Details |
| :------------ | :------ |
| Unterstützung der UTF-8-Servercodierung | [UTF-8-Unterstützung im OLE DB-Treiber für SQL Server](features/utf-8-support-in-oledb-driver-for-sql-server.md). |
| Unterstützung für die Azure Active Directory-Authentifizierung. | [Verwenden von Azure Active Directory](features/using-azure-active-directory.md). |
| &nbsp; | &nbsp; |

## <a name="1810"></a>18.1.0

![Download](../../ssms/media/download-icon.png) [Herunterladen des x64-Installationsprogramms](https://go.microsoft.com/fwlink/?linkid=2118506)  
![Download](../../ssms/media/download-icon.png) [Herunterladen des x86-Installationsprogramms](https://go.microsoft.com/fwlink/?linkid=2118509)  

Veröffentlichung: Juli 2018

Wenn Sie das Installationsprogramm in einer anderen Sprache als der für Sie erkannten herunterladen möchten, können Sie hierfür einen der folgenden direkten Links verwenden.  
Für den x64-Treiber: [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x40a)  
Für den x86-Treiber: [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2118509&2118509=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x40a)  

### <a name="features-added-in-1810"></a>In 18.1.0 hinzugefügte Features

| Neues Feature | Details |
| :------------ | :------ |
| Unterstützung für das Schlüsselwort der `UseFMTONLY`-Verbindungszeichenfolge sowie für die Initialisierungseigenschaft `SSPROP_INIT_USEFMTONLY`. | `UseFMTONLY` steuert, wie Metadaten abgerufen wird, wenn eine Verbindung mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher hergestellt wird.<br/><br/>Weitere Informationen finden Sie unter [Verwenden von Schlüsselwörtern für Verbindungszeichenfolgen mit dem OLE DB-Treiber für SQL Server.](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md) |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed-in-1810"></a>In 18.1.0 behobene Fehler

| Behobene Fehler | Details |
| :-------- | :------ |
| Die falsche Version der BCP-Formatdatei wurde korrigiert. | Der OLE DB-Treiber 18.0 legt fälschlicherweise die Version der BCP-Formatdatei auf 18.0 statt auf 11.0 fest.<br/>Die Formatdateien, die vom OLE DB-Treiber 18.0 generiert wurden, können nicht vom OLE DB-Treiber 18.1 gelesen werden.<br/>Wenn Sie mit dem neuen Treiber Formatdateien verwenden müssen, die von der vorherigen Treiberversion generiert wurden, können Sie diese Dateien manuell bearbeiten, um die Version in 11.0 zu ändern. |
| &nbsp; | &nbsp; |

## <a name="1802"></a>18.0.2

![Download](../../ssms/media/download-icon.png) [Herunterladen des x64-Installationsprogramms](https://go.microsoft.com/fwlink/?linkid=2118504)  
![Download](../../ssms/media/download-icon.png) [Herunterladen des x86-Installationsprogramms](https://go.microsoft.com/fwlink/?linkid=2118277)  

Veröffentlichung: März 2018

Wenn Sie das Installationsprogramm in einer anderen Sprache als der für Sie erkannten herunterladen möchten, können Sie hierfür einen der folgenden direkten Links verwenden.  
Für den x64-Treiber: [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x40a)  
Für den x86-Treiber: [Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x40a)  

### <a name="features-added-in-1802"></a>In 18.0.2 hinzugefügte Features

| Neues Feature | Details |
| :------------ | :------ |
| Unterstützung für das Schlüsselwort der `MultiSubnetFailover`-Verbindungszeichenfolge sowie für die Initialisierungseigenschaft `SSPROP_INIT_MULTISUBNETFAILOVER`. | Weitere Informationen finden Sie unter<br/>&bull; &nbsp; [OLE DB-Treiber für SQL Server-Unterstützung für Hochverfügbarkeit und Notfallwiederherstellung](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md) und<br/>&bull; &nbsp; [Verwenden von Schlüsselwörtern für Verbindungszeichenfolgen mit dem OLE DB-Treiber für SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Weitere Informationen

[Microsoft OLE DB-Treiber für SQL Server](oledb-driver-for-sql-server.md)
