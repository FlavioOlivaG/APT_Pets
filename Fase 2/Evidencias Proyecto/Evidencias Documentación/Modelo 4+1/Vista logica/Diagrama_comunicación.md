```mermaid
sequenceDiagram
    autonumber

    participant Cliente
    participant Paseador
    participant Administrador
    participant Web as Sistema Web
    participant DB as Base de Datos
    participant Notificación as Servicio de Notificación
    participant Webpay as Servicio de Pago

    %% Épica 1: Gestión de Usuarios y Autenticación
    %% Registro y Autenticación de Usuarios
    alt "Registro y Autenticación de Usuarios"
        Cliente ->> Web: Acceder y navegar por la página web
        Cliente ->> Web: Registrarse como cliente
        Paseador ->> Web: Registrarse y postular como Paseador
        Web -->> Cliente: Confirmación de registro
        Web -->> Paseador: Notificación de aprobación de postulación
        Cliente ->> Web: Iniciar sesión como cliente
        Paseador ->> Web: Iniciar sesión como paseador
    end

    %% Épica 2: Perfil y Gestión de Información Personal
    %% Gestión de Perfiles y Mascotas
    alt "Gestión de Perfiles y Mascotas"
        Cliente ->> Web: Editar perfil e información personal
        Cliente ->> Web: Registrar mascota
        Paseador ->> Web: Editar perfil e información personal
        Paseador ->> Web: Establecer disponibilidad horaria
    end

    %% Épica 3: Búsqueda y Visualización de Servicios
    %% Exploración de Paseadores y Reservas
    alt "Exploración de Paseadores y Reservas"
        Cliente ->> Web: Visualizar paseadores y tarifas
        Cliente ->> Web: Enviar solicitud de reserva de paseo
        Paseador ->> Web: Revisar solicitudes de paseo
    end

    %% Épica 4: Gestión de Reservas y Servicios
    %% Gestión de Reservas y Servicios
    alt "Gestión de Reservas y Servicios"
        Cliente ->> Web: Cancelar reserva de paseo
        Paseador ->> Web: Rechazar solicitud de paseo
        Paseador ->> Web: Aceptar y agendar solicitud de paseo
        Cliente ->> Webpay: Realizar pago
        Cliente ->> Web: Visualizar paseos agendados
        Paseador ->> Web: Visualizar paseos agendados
        Cliente ->> Web: Chatear con paseador
        Paseador ->> Web: Chatear con cliente
    end

    %% Épica 5: Notificaciones y Confirmaciones de Servicio
    %% Confirmación y Seguimiento del Servicio
    alt "Confirmación y Seguimiento del Servicio"
        Paseador ->> Cliente: Confirmar inicio de servicio
        Cliente ->> Paseador: Notificación de inicio de servicio
        Paseador ->> Cliente: Confirmar llegada al lugar
        Paseador ->> Cliente: Reportar estado del servicio y ubicación
        Cliente ->> Paseador: Monitorear estado del paseo y ubicación
        Paseador ->> Cliente: Informar entrega de la mascota
        Cliente ->> Paseador: Confirmar trabajo realizado
    end

    %% Épica 6: Evaluación y Pagos
    %% Calificación y Transacciones
    alt "Calificación y Transacciones"
        Cliente ->> Web: Calificar el servicio del paseo
        Paseador ->> Webpay: Retirar el pago por el servicio
        Paseador ->> Web: Revisar calificación del paseo
    end

    %% Épica 7: Gestión de incidencias
    %% Reportes y Protocolos
    alt "Reportes y Protocolos"
        Cliente ->> Web: Reportar incidencia
        Paseador ->> Web: Reportar incidencia
        Administrador ->> Web: Visualizar reportes de paseadores existentes
        Administrador ->> Web: Banear cuenta de cliente
        Administrador ->> Web: Banear cuenta de paseador
        Administrador ->> Web: Iniciar protocolo de emergencia
    end

    %% Épica 8: Administración y Gestión del Sistema
    %% Administración de la Plataforma
    alt "Administración de la Plataforma"
        Administrador ->> Web: Gestionar cuentas de usuario
        Administrador ->> Web: Gestionar roles y permisos de usuarios
        Administrador ->> Web: Ver informes de actividades y uso del sistema
        Administrador ->> Web: Visualizar reportes de clientes existentes
    end
