# eIDReader

Librería basada en Swift que permite las siguientes opciones:
- Uso del DNIe Español, implementando las siguientes funcionalidades:
    - Lectura de datos públicos del DNIe.    
- Uso de cualquier documento electrónico de identidad que cumpla las normas ICAO (pasaportes o documentos nacionales de identidad), permitiendo la lectura de sus datos públicos.

---

[Requisitos](#requisitos) | [Funcionalidades](#funcionalidades) | [Instalación](#instalacion) | [Autor](#autor) | [Licencia](#licencia)

## Requisitos
Esta librería está disponible para en ios 14 o posterior.
Esta librería permite la comunicación entre un dispositivo móvil y el DNIe Español u otros documentos electrónicos de identidad, mediante el uso de NFC. Es por ello que esta librería sólo puede ser usada en dispositivos móvil provistos de tecnología NFC, esta tecnología está disponible en todos los iphone a partir de iphone 7.

Esta librería tiene las siguientes dependencias:
- OpenSSL (https://github.com/krzyzanowskim/OpenSSL.git) -> versón 1.1.1900
- CryptoSwift (https://github.com/krzyzanowskim/CryptoSwift.git) -> versión 1.6.0

## Funcionalidades
Esta librería ofrece las siguientes funcionalidades:
### Lectura de datos públicos del DNIe o cualquier documento electrónico de identidad:
#### Utilizando can para establecer canal seguro.
```Swift
        passportReader.readPassport(accessKey: can, paceKeyReference: PACEHandler.CAN_PACE_KEY_REFERENCE, tags: [], skipSecureElements: true, customDisplayMessage: { (displayMessage) in  return NFCUtils.customDisplayMessage(displayMessage: displayMessage)
        }, completed: { (passport, error) in
            if let passport = passport {            
                //passport contiene todos los datos del DNIe
            } else {
                //procesamos error
                print("Error: \(error?.localizedDescription)")
            }
        })
    }
```

#### Utilizando mrz para establecer canal seguro.    
```Swift
        passportReader.readPassport(accessKey: mrzKey, paceKeyReference: PACEHandler.MRZ_PACE_KEY_REFERENCE, tags: [], skipSecureElements: true, customDisplayMessage: { (displayMessage) in
        return NFCUtils.customDisplayMessage(displayMessage: displayMessage)
        }, leeCertificadosPublicos: false, completed: { (passport, error) in
            if let passport = passport {            
                //passport contiene todos los datos del DNIe
            } else {
                //procesamos error
                print("Error: \(error?.localizedDescription)")
            }
        })
    }
```    

## Instalación

### Swift Package Manager

eIDReader.swift es compatible con Swift Package Manager v4 (Swift 4 and above). Simplemente añádela a las dependencias en tu `Package.swift`.

```Swift
dependencies: [
    .package(url: "https://github.com/diegocidm4/eIDReader.git", from: "1.0.0")
]
```

Después de esto, podrás importarla en tus ficheros `.swift`.

```Swift
import eIDReader
```

## Autor

eIDReader ha sido creada y mantenida por [Diego Cid]

Puede seguirme en Twitter en [@diegocidm4](http://twitter.com/diegocidm4).

## Licencia
La librería se distribuye con una licencia anual asociada a un app bundle.
