---
author: MikeRayMSFT
ms.prod: sql
ms.topic: include
ms.date: 01/07/2020
ms.author: mikeray
ms.openlocfilehash: 0c15fb58bb076724402ab72f81e58ce46c8b7b1e
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257400"
---
### <a name="pythonpip-installation"></a>Python-/pip-Installation

Sie können [!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)] unter Linux mit yum, apt oder zypper und unter macOS mit Homebrew-Paket-Managern installieren. Bevor diese Paket-Manager zur Verfügung standen, wurden Python und pip für die Installation benötigt.

>[!IMPORTANT]
>Bevor Sie fortfahren, müssen Sie alle Installationen von `azdata` aus dem globalen Python-System entfernen. Die neuen Installer oder nativen Pakete fügen `azdata` zu Ihrem Pfad hinzu, und es ist nicht möglich, die erste Installation zu ermitteln.
Wenn `azdata` bereits im globalen Python-System installiert ist, entfernen Sie diese Installation, bevor Sie fortfahren.

Führen Sie den folgenden Befehl aus, um die aktuelle Installation aufzurufen:

```bash
$ pip list --format columns
```

Wenn `azdata` von pip installiert wurde, werden das Paket und die Version zurückgegeben. Beispiel:

```
 Package             Version
------------------- ----------
azdata-cli          15.0.X
azdata-cli-app      15.0.X
azdata-cli-cluster  15.0.X
azdata-cli-core     15.0.X
azdata-cli-hdfs     15.0.X
azdata-cli-notebook 15.0.X
azdata-cli-profile  15.0.X
azdata-cli-spark    15.0.X
azdata-cli-sql      15.0.X
```

Im folgenden Beispiel wird eine pip-Installation von `azdata` entfernt.

```bash
$ pip freeze | grep azdata-* | xargs pip uninstall -y
```

Nachdem Sie überprüft haben, dass Sie alle Installationen von `azdata` entfernt haben, die mit pip installiert wurden, fahren Sie mit der Installation fort.