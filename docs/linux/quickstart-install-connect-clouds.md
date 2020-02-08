---
title: Erste Schritte mit SQL Server (für Linux) in der Cloud
titleSuffix: SQL Server
description: Dieser Schnellstart veranschaulicht das Ausführen von SQL Server unter Linux in einer Cloud Ihrer Wahl.
author: VanMSFT
ms.author: vanto
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 402466ab44a5f3795c0031ecdaa33cb863279839
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "73594558"
---
# <a name="quickstart-run-sql-server-in-the-cloud"></a>Schnellstart: Ausführen von SQL Server in der Cloud
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Schnellstart installieren Sie SQL Server unter Red Hat Enterprise Linux (RHEL), SuSE Linux Enterprise Server (SLES) oder Ubuntu in der Cloud Ihrer Wahl. Lesen Sie [Bereitstellen eines virtuellen SQL Server-Computers über das Azure-Portal](https://docs.microsoft.com/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json), wenn Sie SQL Server für Linux in Azure ausführen möchten.

> [!NOTE]
> Wenn Sie eine kostenpflichtige Edition von SQL Server ausführen möchten, müssen Sie Ihre eigene Lizenz (BYOL) verwenden.

## <a name="amazon-web-services"></a>Amazon Web Services
1.  Erstellen Sie ein Linux-AMI mit mindestens 2 GB Arbeitsspeicher aus dem Marketplace. 
    * [RHEL 7.3+](https://aws.amazon.com/marketplace/pp/B00KWBZVK6)
    * [SLES v12 SP2 und höher](https://aws.amazon.com/marketplace/pp/B00PMM99PI)
    * [Ubuntu 16.04](https://aws.amazon.com/marketplace/pp/B01JBL2M0O)
1.  Stellen Sie über SSH eine Verbindung mit dem AMI her.
1.  Gehen Sie entsprechend dem Schnellstart für die von Ihnen ausgewählte Linux-Distribution vor: 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Konfigurieren Sie für Remoteverbindungen: 
    * Öffnen Sie die [Amazon EC2-Konsole]( https://console.aws.amazon.com/ec2/).
    * Wählen Sie im Navigationsbereich die Option **Security Groups** aus. 
    * Wählen Sie **Inbound, Edit, Add Rule** aus.
    * Fügen Sie eine eingehende Regel hinzu, um Datenverkehr an dem Port zuzulassen, an dem SQL Server lauscht (standardmäßig TCP-Port 1433).

    
## <a name="digital-ocean"></a>Digital Ocean
1. Melden Sie sich über das [Anmeldefenster](https://cloud.digitalocean.com/login) an, und klicken Sie auf „Create a droplet“.
1. Wählen Sie ein Ubuntu 16.04-Droplet mit mindestens 2 GB Arbeitsspeicher aus.
1. Stellen Sie über SSH eine Verbindung mit dem Droplet her.
1. Gehen Sie entsprechend dem [Ubuntu-Schnellstart](quickstart-install-connect-ubuntu.md) vor.
1. Konfigurieren Sie für Remoteverbindungen:
    * Klicken Sie oben in der Systemsteuerung auf den Link **Networking**, und wählen Sie dann **Firewalls** aus.
    * Fügen Sie eine eingehende Regel hinzu, um Datenverkehr an dem Port zuzulassen, an dem SQL Server lauscht (standardmäßig TCP-Port 1433).
    
## <a name="google-cloud-platform"></a>Google Cloud Platform
1.  Erstellen Sie ein Linux-Image mit mindestens 2 GB Arbeitsspeicher aus dem Cloud Launcher. 
    * [RHEL 7.3+](https://console.cloud.google.com/launcher/details/rhel-cloud/rhel-7)
    * [SLES v12 SP4](https://console.cloud.google.com/launcher/details/suse-cloud/sles-12)
    * [Ubuntu 16.04](https://console.cloud.google.com/launcher/details/ubuntu-os-cloud/ubuntu-xenial)
1.  Stellen Sie über SSH eine Verbindung mit dem Image her.
1.  Gehen Sie entsprechend dem Schnellstart für die von Ihnen ausgewählte Linux-Distribution vor: 
    * [RHEL](quickstart-install-connect-red-hat.md)
    * [SLES](quickstart-install-connect-suse.md)
    * [Ubuntu](quickstart-install-connect-ubuntu.md)
1.  Konfigurieren Sie für Remoteverbindungen: 
    * Öffnen Sie [Firewallregeln](https://console.cloud.google.com/networking/firewalls).
    * Fügen Sie eine eingehende Regel hinzu, um Datenverkehr an dem Port zuzulassen, an dem SQL Server lauscht (standardmäßig TCP: 1433).
