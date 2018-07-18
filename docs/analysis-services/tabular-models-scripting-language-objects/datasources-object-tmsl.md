---
title: DataSources-Objekt (TMSL) | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7beabaaf63194cc699c3711a87dd1e59d244c068
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38981332"
---
# <a name="datasources-object-tmsl"></a>DataSources-Objekt (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Definiert eine Verbindung mit einer Datenquelle, die vom Modell entweder während des Imports zum Hinzufügen von Daten für das Modell oder im Pass-through-Abfragen über DirectQuery-Modus verwendet werden.  Modelle im DirectQuery-Modus nur möglich, eine **DataSource** Objekt.  
  
 Es sei denn, Sie erstellen, und Ersetzen Sie dabei, oder ändern das Objekt selbst, alle Datenquellen in Ihrem Skript (z. B. in der Partition Skripts) auf die verwiesen wird. muss einer vorhandenen **DataSource** Objekt in Ihrem Modell.  
  
## <a name="object-definition"></a>Objektdefinition  
 Alle Objekte verfügen über einen gemeinsamen Satz von Eigenschaften, einschließlich Name, Typ, Beschreibung, eine eigenschaftsauflistung und Anmerkungen. **DataSource** Objekte verfügen außerdem über die folgenden Eigenschaften.  
  
 Typ  
 Der DataSource-Typ. Derzeit ist der einzige gültige Wert Provider (1) - normale Verbindungszeichenfolge.  
  
 connectionString  
 Die Verbindungszeichenfolge, die minimal gibt den Server und die Datenbank, jedoch kann auch andere Eigenschaften, die von der externen RDBMS, z. B. eine Daten-Anbieter oder ein Benutzerkonto unterstützt werden. Dieser Wert ist erforderlich. Finden Sie unter [SqlConnectionStringBuilder-Klasse](https://msdn.microsoft.com/library/ms254500\(v=vs.110\).aspx) ausführliche Informationen zu SQL Server-Datenbank-Verbindungszeichenfolgen-Eigenschaften.  
  
 impersonationMode  
 Gibt an, ob Analysis Services die Identität des Benutzers, der die Abfrage anfordert Identitätswechsel verwenden soll. Diese Eigenschaft ist ein numerischer Wert, der angibt, die Anmeldeinformationen für den Identitätswechsel verwenden. Folgende Enumerationswerte sind möglich:  
  
-   Standard (1) - Server verwendet die identitätswechselmethode, die er hält, für den Kontext geeignet zu sein, die in der Identitätswechsel verwendet wird.  
  
-   ImpersonateAccount (2): verwendet der Server das angegebene Benutzerkonto an.  
  
-   ImpersonateAnonymous (3): verwendet der Server das anonyme Benutzerkonto.  Diese Option wird nicht empfohlen, aber Sie wird manchmal in HTTP-Szenarien durch benutzerdefinierte Anwendungen, die Authentifizierung verwendet.  
  
-   ImpersonateCurrentUser (4) - verwendet der Server das Benutzerkonto, dem der Client als eine Verbindung herstellt.  
  
-   ImpersonateServiceAccount (5) – verwendet der Server das Benutzerkonto, dem als der Server ausgeführt wird.  
  
-   ImpersonateUnattendedAccount (6) – verwendet der Server ein unbeaufsichtigtes Benutzerkonto an. Dies wird für Power Pivot oder tabellarische Modelle verwendet, die in einer SharePoint-Umgebung ausgeführt.  
  
 DirectQuery-Modus kann ImpersonateCurrentuser verwenden, wenn Analysis Services für die vertrauenswürdige Delegierung konfiguriert ist oder  
                      ImpersonateServiceAccount, wenn die abfrageanforderung im Sicherheitskontext des Analysis Services-Dienstkontos ausgeführt wird. Finden Sie unter [Configure Analysis Services for Kerberos eingeschränkte Delegierung](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md).  
  
 account  
 Für den Identitätswechsel verwendet. Eine Windows oder das Datenbankkonto, die einen gültigen Anmeldenamen mit Leseberechtigungen für die externe Datenbank an.  
  
 Kennwort  
 Eine verschlüsselte Zeichenfolge, die das Kennwort des Kontos.  
  
 maxConnections  
 Die maximale Anzahl von gleichzeitig mit der Datenquelle zu öffnenden Verbindungen.  
  
 isolation  
 Die Art der Isolation, die beim Ausführen von Befehlen für die Datenquelle verwendet wird. Gültige Werte sind "ReadCommitted" (1) oder Momentaufnahme (2).  
  
 timeout  
 Eine ganze Zahl, die angibt, das Timeout in Sekunden für Befehle, die für die Datenquelle ausgeführt.  
  
 Provider  
 Eine optionale Zeichenfolge, die den Namen des verwalteten Datenanbieters für die Verbindung mit der relationalen Datenbank verwendet, wenn nicht anders angegeben, für die Verbindungszeichenfolge identifiziert.  
  
## <a name="usage"></a>Verwendung  
 **DataSource** Objekte dienen in [Alter-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md), [Erstellungsbefehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md), [CreateOrReplace-Befehl &#40; TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md), [Löschbefehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md), [Refresh-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md), und [MergePartitions-Befehl &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md).  
  
 Ein **DataSource** Objekt ist eine Eigenschaft eines Modells, aber es kann auch als Eigenschaft eines Datenbankobjekts, erhält die 1: 1-Zuordnung zwischen Modell und Datenbank angegeben werden.  Geben Sie die Partitionen basierend auf der SQL-Abfragen auch eine **DataSource**, nur für einen reduzierten Satz von Eigenschaften.  
  
 Beim Erstellen, ersetzen oder ändern ein Datenquellenobjekt, geben Sie alle Lese-/ Schreibeigenschaften der Objektdefinition. Unterdrücken einer Lese-/ Schreibzugriff-Eigenschaft wird einen Löschvorgang betrachtet.  
  
## <a name="examples"></a>Beispiele  
 **Beispiel 1** -eine Verbindung mit einem *FoodMart* Datenbank auf einer benannten Instanz von *Sales* auf einem Netzwerkserver, die mit dem Namen *"SERVER01"*.  
  
```  
"dataSources": [  
      {  
        "name": "SqlServer Server01 FoodMart",  
        "connectionString": "Provider=SQLNCLI11;Data Source=Server01\Sales;Initial Catalog=Foodmart;Integrated Security=SSPI;Persist Security Info=false",  
        "impersonationMode": "impersonateServiceAccount",  
      }  
]  
```  
  
## <a name="full-syntax"></a>Vollständige Syntax  
 Im folgenden finden Sie die Zeichenfolgendarstellung von Schema für ein Datenquellenobjekt eines Modells.  
  
```  
"dataSources": {  
          "type": "array",  
          "items": {  
            "anyOf": [  
              {  
                "description": "ProviderDataSource object of Tabular Object Model (TOM)",  
                "type": "object",  
                "properties": {  
                  "name": {  
                    "type": "string"  
                  },  
                  "description": {  
                    "type": "string"  
                  },  
                  "type": {  
                    "enum": [  
                      "provider"  
                    ]  
                  },  
                  "connectionString": {  
                    "type": "string"  
                  },  
                  "impersonationMode": {  
                    "enum": [  
                      "default",  
                      "impersonateAccount",  
                      "impersonateAnonymous",  
                      "impersonateCurrentUser",  
                      "impersonateServiceAccount",  
                      "impersonateUnattendedAccount"  
                    ]  
                  },  
                  "account": {  
                    "type": "string"  
                  },  
                  "password": {  
                    "type": "string"  
                  },  
                  "maxConnections": {  
                    "type": "integer"  
                  },  
                  "isolation": {  
                    "enum": [  
                      "readCommitted",  
                      "snapshot"  
                    ]  
                  },  
                  "timeout": {  
                    "type": "integer"  
                  },  
                  "provider": {  
                    "type": "string"  
                  },  
                  "annotations": {  
                    "type": "array",  
                    "items": {  
                      "description": "Annotation object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "name": {  
                          "type": "string"  
                        },  
                        "value": {  
                          "anyOf": [  
                            {  
                              "type": "string"  
                            },  
                            {  
                              "type": "array",  
                              "items": {  
                                "type": "string"  
                              }  
                            }  
                          ]  
                        }  
                      },  
                      "additionalProperties": false  
                    }  
                  }  
                },  
                "additionalProperties": false  
              }  
            ]  
          }  
        },  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Tabular Model Scripting Language &#40;TMSL&#41; – Referenz](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [DirectQuery-Modus](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Konfigurieren von HTTP-Zugriff auf Analysis Services unter Internetinformationsdienste &#40;IIS&#41; 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
