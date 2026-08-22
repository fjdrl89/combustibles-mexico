# Ventas de combustibles en México

Sitio estático con el diagnóstico independiente del mercado mexicano de combustibles, con datos a
julio de 2026. Es una carpeta de archivos sueltos, sin servidor ni base de datos: se publica copiando
su contenido a cualquier hosting estático.

| Archivo | Qué es |
| --- | --- |
| `index.html` | Portada con el resumen, las cifras principales y las ligas a todo lo demás |
| `tablero.html` | Tablero interactivo, catorce secciones con el diagnóstico completo |
| `cuaderno.html` | Cuaderno técnico, el detalle metodológico y el bloque de IEPS |
| `Nota_Ventas_Combustibles.pdf` y `.docx` | La nota ejecutiva |
| `Ventas_Combustibles_Mexico.xlsx` | Libro de trabajo con veinte hojas y las fórmulas vivas |
| `.nojekyll` | Archivo vacío que le pide a GitHub Pages servir los archivos tal cual. Es opcional en este sitio |
| `robots.txt` | Le pide a los buscadores no indexar el sitio |

Los dos tableros son autocontenidos: traen adentro los datos, el motor de gráficas y los estilos. Lo
único que piden a la red es la hoja de tipografías de Google, y si no carga el sitio se ve bien de
todos modos con las tipografías del sistema.

Para revisarlo antes de publicar nada, basta abrir `index.html` con doble clic. Funciona igual del
disco que en línea.

---

## Antes de publicar: qué tan visible queda

GitHub Pages publica hacia afuera. Conviene tenerlo claro antes de subir nada:

- Con plan **Free** el repositorio tiene que ser **público** para poder activar Pages.
- Con **Pro** o **Team** se puede publicar desde un repositorio privado, pero **el sitio publicado
  sigue siendo accesible para cualquiera que tenga la dirección**. El repositorio queda privado; la
  página, no.
- Restringir el acceso al sitio mismo, de modo que sólo entre quien tenga permiso en el repositorio,
  existe únicamente en **Enterprise Cloud**.

Como freno suave, todas las páginas llevan la etiqueta `noindex` y hay un `robots.txt` que pide a los
rastreadores no indexar nada. Eso evita que el material aparezca en un buscador, pero **no es
seguridad**: cualquiera con la dirección puede abrirlo. Si el material no puede salir de la
institución, la ruta correcta no es GitHub Pages sino un sitio con autenticación, por ejemplo Azure
Static Web Apps contra el directorio de la institución, o un servidor interno. Esta misma carpeta
sirve para cualquiera de esas opciones sin cambiarle nada.

---

## Ruta A. Desde el navegador, sin instalar nada

Es la más simple y no requiere git ni ningún programa. Toma unos diez minutos la primera vez.

### 1. Tener cuenta

Si no tienes, se crea en `github.com` con correo y contraseña. Conviene usar el correo institucional
sólo si la institución ya administra cuentas de GitHub; si no, uno personal está bien.

### 2. Crear el repositorio

1. Arriba a la derecha, el botón **+** y luego **New repository**.
2. En **Repository name** escribe un nombre sin espacios ni acentos, por ejemplo
   `combustibles-mexico`. Ese nombre aparecerá en la dirección del sitio.
3. Elige **Public** o **Private**. Recuerda lo de arriba: con plan Free tiene que ser público para
   que Pages funcione, y aun en privado la página publicada queda accesible para quien tenga la liga.
4. **No** marques *Add a README file*, porque la carpeta ya trae uno.
5. Botón verde **Create repository**.

### 3. Subir los archivos

1. En la página que aparece, busca la liga **uploading an existing file**. Si no la ves, usa el botón
   **Add file** y luego **Upload files**.
2. Abre en el explorador de Windows la carpeta `sitio`.
3. **Entra a la carpeta y selecciona todo lo que hay adentro** con Ctrl+A. Este paso es el que más se
   equivoca: hay que arrastrar **el contenido**, no la carpeta. Si arrastras la carpeta completa,
   GitHub crea un subdirectorio `sitio/` adentro del repositorio y el sitio no encuentra su portada.
4. Arrastra la selección a la zona de la página que dice *Drag files here*.
5. Espera a que terminen de subir. Son unos 4 MB en total, así que tarda poco. El límite del
   navegador es de 25 MB por archivo y 100 archivos por vez, y aquí son nueve archivos y el más
   pesado no llega a 1.5 MB.
6. Abajo, botón verde **Commit changes**.

Si Windows tiene ocultos los archivos que empiezan con punto, `.nojekyll` no se va a subir. **No
pasa nada**: en este sitio ese archivo es opcional, porque ningún archivo empieza con guion bajo ni
contiene sintaxis de plantillas, que es lo único que Jekyll podría estropear. Si aun así lo quieres,
se crea en veinte segundos: botón **Add file**, luego **Create new file**, escribe `.nojekyll` como
nombre, deja el contenido vacío y dale **Commit changes**.

### 4. Encender GitHub Pages

1. En el repositorio, pestaña **Settings**, arriba a la derecha.
2. En la barra de la izquierda, sección *Code and automation*, entra a **Pages**.
3. En **Build and deployment**, deja *Source* en **Deploy from a branch**.
4. En *Branch*, elige **main** y, en el desplegable de al lado, la carpeta **`/ (root)`**.
5. Botón **Save**.

### 5. Abrir el sitio

Refresca esa misma pantalla al cabo de un minuto o dos. Arriba aparece un recuadro con la dirección,
que será algo como `https://TU-USUARIO.github.io/combustibles-mexico/`. El primer despliegue puede
tardar hasta diez minutos; los siguientes son de uno o dos.

### 6. Actualizar después

Cuando haya una versión nueva del análisis:

1. Entra al repositorio, **Add file**, **Upload files**.
2. Arrastra otra vez el contenido de la carpeta `sitio`. Los archivos con el mismo nombre se
   reemplazan solos.
3. **Commit changes**.

La dirección no cambia, así que cualquier liga que ya hayas compartido sigue funcionando.

---

## Ruta B. Con GitHub Desktop

Conviene si vas a actualizar el sitio seguido, porque evita subir archivos a mano cada vez.

1. Instala **GitHub Desktop** desde `desktop.github.com` e inicia sesión con tu cuenta.
2. Menú **File**, **New repository**. Ponle nombre y elige una carpeta local donde vivirá.
3. Copia dentro de esa carpeta todo el contenido de `sitio`.
4. En GitHub Desktop aparecen los archivos como cambios pendientes. Escribe un mensaje abajo a la
   izquierda, por ejemplo *Sitio del diagnóstico de combustibles*, y dale **Commit to main**.
5. Botón **Publish repository** arriba. Ahí eliges si queda público o privado.
6. Sigue el paso 4 de la ruta A para encender Pages.

Para actualizar: reemplazas los archivos en la carpeta local, y en GitHub Desktop das **Commit to
main** y luego **Push origin**.

---

## Ruta C. Línea de comandos

Si ya tienes git instalado:

```bash
cd sitio
git init -b main
git add .
git commit -m "Sitio del diagnóstico de combustibles, datos a julio de 2026"
git remote add origin https://github.com/TU-USUARIO/combustibles-mexico.git
git push -u origin main
```

Y luego el paso 4 de la ruta A para encender Pages. Para actualizar, `git add .`, `git commit -m
"..."` y `git push`.

---

## Si algo no se ve

- **Sale una página de error 404.** Casi siempre es que se arrastró la carpeta en vez de su
  contenido, así que `index.html` quedó dentro de un subdirectorio. Se comprueba mirando la lista de
  archivos del repositorio: `index.html` tiene que estar en el primer nivel. Si quedó dentro de una
  carpeta, la solución rápida es renombrarla a `docs` y elegir `/docs` en la pantalla de Pages.
- **La página sale sin estilos o con el texto crudo.** Es el caso raro en que hace falta `.nojekyll`.
  Se crea como se explica en el paso 3.
- **Los cambios no aparecen.** Suele ser caché del navegador. Recarga con Ctrl+F5, o abre la
  dirección en una ventana privada.
- **Pages no aparece en Settings.** Ocurre cuando el repositorio es privado y la cuenta está en plan
  Free. O se hace público, o se sube el plan, o se publica en otro lado.

---

## Publicar en otro lado

La carpeta funciona igual en cualquier hosting estático. Sólo hay que copiar su contenido:

- **Azure Static Web Apps.** Es la opción con autenticación: se puede exigir cuenta del directorio de
  la institución para entrar. Requiere una suscripción de Azure.
- **Un servidor interno.** Copiar la carpeta al directorio que sirva el servidor web. No hace falta
  configurar nada más, porque no hay código de servidor.
- **Abrirla del disco.** Los archivos funcionan con doble clic, sin servidor.

---

## Cómo se regenera

El sitio no se edita a mano. Sale de `src/sitio.py` dentro del paquete de análisis, que toma los dos
tableros y los documentos ya generados, los envuelve en documentos HTML completos y arma la portada
leyendo las cifras del mismo archivo de datos que alimenta los tableros. Así la portada no puede
desincronizarse de los tableros.

```bash
python3 src/sitio.py
```

---

## Límites que conviene conocer

GitHub Pages admite hasta 1 GB de sitio y tiene un límite blando de 100 GB de tráfico al mes. Este
sitio pesa alrededor de 4 MB en total, así que sobra espacio por mucho.

---

**Fuentes.** Venta en la bomba, distribución, comercialización, autoconsumo y precios: Comisión
Nacional de Energía. Ventas internas, elaboración y exportaciones: Petróleos Mexicanos. Importaciones:
Sistema de Información Energética, SENER. Índice de precios y actividad económica: Banco de México.
Recaudación observada e impuesto al carbono: Secretaría de Hacienda y Crédito Público. Cifras
auditadas: Pemex, Formulario 20-F 2025.
