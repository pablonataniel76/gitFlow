**GIT FLOW**

Git Flow es un flujo de trabajo aplicado a un repositorio Git. [Vincent Driessen](https://nvie.com/posts/a-successful-git-branching-model/) fue el encargado de popularizarlo, definiendo un modelo estricto de ramificación diseñado en torno a los lanzamientos del proyecto. Es ideal para proyectos que lleven una planificación de entregas iterativas. Permite la paralelización del desarrollo mediante ramas independientes para la preparación, mantenimiento y publicación de versiones del proyecto, así como soporta la reparación de errores en cualquier momento.

**RAMAS PRINCIPALES**

Todo proyecto, por defecto, debería tener al menos dos ramas infinitas para su desarrollo. Esta metodología define que deben existir dos ramas principales:

- Master

Contiene cada una de las versiones estables del proyecto. Cualquier commit que subamos en esta rama debe estar preparado para que se pueda incluir en producción.

- Develop

Contiene el código de desarrollo de la siguiente versión planificada del proyecto. En ella se incluirán cada una de las nuevas características que se desarrollen. Esta rama puede incorporarse tanto en una rama release como en la rama *master*, para su despliegue en producción.

Cabe destacar que nunca se debería modificar código directamente en alguna de estas dos ramas.

**RAMAS DE APOYO**

Junto a las ramas master y develop, existe un conjunto de ramas de apoyo, su objetivo es el permitir el desarrollo en paralelo entre los miembros del equipo, la resolución de problemas en producción de forma rápida, etc. A diferencia de las ramas principales, estas están limitadas en tiempo. Serán eliminadas eventualmente. Los diferentes tipos de ramas que se usarán son:

- Feature

Estas ramas tienen que surgir de la rama develop. Cada una de estas ramas almacenan código de desarrollo con nuevas características. Típicamente existen solamente en los repositorios locales de los desarrolladores y no en el repositorio origen. Una vez terminado su desarrollo, se incorporarán nuevamente a la rama develop, que contendrá la última versión de código en desarrollo.

- Release

Como las ramas feature, las ramas release también tienen que surgir de la rama develop. Contienen el código de la versión que se va a liberar próximamente. Es un paso previo y preparatorio para la versión definitiva de producción. En ella se incluye todo el código de develop necesario para el lanzamiento. Puede que contenga algún error pequeño que se debe de arreglar en este momento para no incluirlo en producción. Una vez finalizada la rama, esta se debe incluir tanto en la rama develop como en la rama *master*.

- Hotfix

Estas ramas surgen de la rama master. Contienen una versión de producción con un error que se desea arreglar urgentemente. Una vez arreglado el error, se incluye el contenido de esta rama en las ramas master y develop para subsanar el error. Además, hay que marcar la versión arreglada de producción con un tag en la rama master.

**GIT BRANCH MODEL**

Las estrategias de git branching permiten que una base de código evolucione orgánicamente de manera coherente. Una estrategia de branching es una convención, o un conjunto de reglas, que describe cuándo se crean las ramas, las pautas de denominación para las ramas, qué uso deben tener las ramas, etc. Las estrategias de branching permiten la separación del trabajo agrupado por ideas conceptuales. Estas ideas conceptuales se pueden desarrollar en paralelo y también pueden implicar correcciones de errores y parches. Existen varias estrategias de branching de Git, como

- Estrategia de implementación programada -- Gitflow

Este flujo de trabajo comienza inicialmente con una única rama de desarrollo. Los desarrolladores crean ramas de características para cada característica o un grupo de características en las que trabajan. Una característica también puede ser una corrección de errores o un refactorizador. El nombre de la rama de características indica la característica en la que se está trabajando. Las ramas de características se fusionan con la rama de desarrollo. Una vez que una masa crítica o un conjunto de características relacionadas se crean y fusionan, se crea una nueva rama de lanzamiento. El equipo puede continuar trabajando en otras funciones mientras se prueba la versión y se registran los defectos. Los defectos se reparan en la rama de liberación y se fusionan nuevamente en la rama de desarrollo. Las nuevas características creadas después de la creación de la rama de lanzamiento también están comprometidas con la rama de desarrollo.

Una vez que el equipo ha confirmado que la calidad del lanzamiento es buena, se crea una nueva rama maestra a partir de la rama de lanzamiento. La rama maestra se etiqueta con la versión y se implementa en producción. Si se identifica un defecto de producción después del lanzamiento, se crea una rama de revisión a partir de la rama de producción y el defecto se repara y se fusiona nuevamente en el maestro para ser etiquetado y lanzado a producción. La revisión también se fusionó nuevamente en la rama de desarrollo. Este flujo de trabajo es una variación de la estrategia de implementación programada.

- Estrategia de implementación de rama por característica -- Github Flow

El flujo de Github fue descrito por primera vez por Scott Chacon. Este flujo de trabajo está optimizado para lanzamientos frecuentes en un modelo de entrega continua. En el flujo de Github solo hay una rama permanente llamada master. Para trabajar en una nueva característica, un desarrollador crea una rama de características desde el maestro y compromete su trabajo a esta rama de características. La rama de funciones se envía al control remoto y se mantiene actualizada regularmente. Cuando se completa el desarrollo de características, el desarrollador emite una solicitud de extracción a la rama maestra. Si se acepta la solicitud de extracción, la característica está lista para implementarse desde la rama de características. Si se despliega la rama de características y no hay problemas, los cambios se fusionan en master. Sin embargo, si hay problemas, el maestro se vuelve a implementar de inmediato, ya que siempre está en un estado de funcionamiento comprobado. Este flujo de trabajo es una variación de la estrategia Branch-Per-Feature deployment .

- Estrategia de ramificación estatal -- Gitlab Flow

El flujo de Gitlab introduce el concepto de ubicación o instantánea para algunas de las ramas. A medida que el código se fusiona de una rama a otra, generalmente se implementa en entornos específicos. Por ejemplo, cuando el código se fusiona desde una rama de características para desarrollar una rama, se implementa en el entorno de desarrollo, cuando el código se fusiona desde una rama de desarrollo a versión, se implementa en un entorno previo a la producción, etc.

El flujo de Gitlab utiliza convenciones de nomenclatura de rama para especificar qué rama se implementa en qué entorno y, lo que es más importante, las condiciones que deben cumplirse antes de implementar una rama en un entorno específico. Esta estrategia de flujo de trabajo es una variación de una estrategia state branching.
