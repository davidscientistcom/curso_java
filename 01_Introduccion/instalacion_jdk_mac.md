<p align="center">
  <img src="../images/banner_eoi.png" width="100%" />
</p>

## Instalación base.

- Instalamos desde brew

```bash
brew install openjdk@21
```

- Lo añadimos al PATH para que lo encuentre:

```bash
echo 'export PATH="/opt/homebrew/opt/openjdk@21/bin:$PATH"' >> ~/.zshrc
echo 'export CPPFLAGS="-I/opt/homebrew/opt/openjdk@21/include"' >> ~/.zshrc
source ~/.zshrc
```

- Vertificamos que esté correctamente instalado

```bash
java -version
```

## Tener múltiples versiones
 
## **1. Instalar múltiples versiones de Java con Homebrew**  
Ejecuta los siguientes comandos para instalar **Java 21 y Java 23**:

```bash
brew install openjdk@21
brew install openjdk@23
```


## **2. Configurar Homebrew para reconocer ambas versiones**  
Cada versión de Java se instala en `/opt/homebrew/opt/openjdk@XX`. Para poder alternarlas fácilmente, necesitamos agregar estas rutas al `PATH`:

Abre tu archivo de configuración de `zsh`:

```bash
nano ~/.zshrc
```

Añade estas líneas al final del archivo:

```bash
export PATH="/opt/homebrew/opt/openjdk@21/bin:$PATH"
export PATH="/opt/homebrew/opt/openjdk@23/bin:$PATH"
```

```bash
source ~/.zshrc
```

### **3. Instalar `jenv` para gestionar versiones de Java**
`jenv` es una herramienta que permite cambiar de versión de Java de forma sencilla.

1. **Instala `jenv`** con Homebrew:

   ```bash
   brew install jenv
   ```

2. **Añade `jenv` al `PATH` y a `zshrc`**:

   ```bash
   echo 'export PATH="$HOME/.jenv/bin:$PATH"' >> ~/.zshrc
   echo 'eval "$(jenv init -)"' >> ~/.zshrc
   source ~/.zshrc
   ```



### **4. Agregar las versiones de Java a `jenv`**
Después de instalar `jenv`, tenemos que decirle qué versiones de Java queremos gestionar. Ejecuta:

```bash
jenv add /opt/homebrew/opt/openjdk@21
jenv add /opt/homebrew/opt/openjdk@23
```

Para verificar las versiones disponibles en `jenv`, usa:

```bash
jenv versions
```

Te debería mostrar algo como:

```
  21
  23
* system (default)
```

### **5. Cambiar de versión de Java según lo necesites**
Para establecer una versión de Java a nivel global (para todo el sistema):

```bash
jenv global 21
```

Para cambiar la versión solo en la terminal actual:

```bash
jenv shell 23
```

Para cambiar la versión solo en un directorio específico (por ejemplo, un proyecto en `/Users/tuusuario/proyecto-java`):

```bash
cd /Users/tuusuario/proyecto-java
jenv local 23
```

Esto crea un archivo `.java-version` dentro del directorio con la versión de Java deseada.


## **6. Verificar que el cambio funciona**
Ejecuta:

```bash
java -version
```

Si cambiaste a la versión 23, deberías ver algo como:

```
openjdk 23 2024-09-19
OpenJDK Runtime Environment (build 23+35)
OpenJDK 64-Bit Server VM (build 23+35, mixed mode)
```

Si cambiaste a la versión 21, verás:

```
openjdk 21 2023-09-19
OpenJDK Runtime Environment (build 21+35)
OpenJDK 64-Bit Server VM (build 21+35, mixed mode)
```

