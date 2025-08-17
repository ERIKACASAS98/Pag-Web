<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TechStore - Tu Tienda de Tecnología Online</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            overflow: hidden;
            margin-top: 20px;
            margin-bottom: 20px;
        }

        /* Banner Superior */
        .banner {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: white;
            padding: 30px 0;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .banner::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="tech" patternUnits="userSpaceOnUse" width="20" height="20"><circle cx="10" cy="10" r="1" fill="rgba(255,255,255,0.1)"/></pattern></defs><rect width="100" height="100" fill="url(%23tech)"/></svg>');
            opacity: 0.3;
        }

        .banner-content {
            position: relative;
            z-index: 2;
        }

        .logo {
            font-size: 3em;
            font-weight: bold;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
            background: linear-gradient(45deg, #fff, #a8d8ea);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .tagline {
            font-size: 1.2em;
            opacity: 0.9;
        }

        /* Menú de Navegación */
        .nav-menu {
            background: #2c3e50;
            padding: 0;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }

        .nav-menu ul {
            list-style: none;
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
        }

        .nav-menu li {
            margin: 0;
        }

        .nav-menu a {
            display: block;
            color: white;
            text-decoration: none;
            padding: 20px 25px;
            transition: all 0.3s ease;
            font-weight: 500;
            position: relative;
            overflow: hidden;
        }

        .nav-menu a::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, #3498db, #2ecc71);
            transition: left 0.3s ease;
            z-index: -1;
        }

        .nav-menu a:hover::before {
            left: 0;
        }

        .nav-menu a:hover {
            transform: translateY(-3px);
            color: white;
        }

        /* Contenido Principal */
        .content {
            padding: 40px;
            min-height: 400px;
        }

        .section {
            display: none;
            animation: fadeIn 0.5s ease-in;
        }

        .section.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .section h2 {
            color: #2c3e50;
            margin-bottom: 25px;
            font-size: 2.5em;
            text-align: center;
            background: linear-gradient(45deg, #3498db, #2ecc71);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .section p {
            margin-bottom: 20px;
            font-size: 1.1em;
            line-height: 1.8;
            text-align: justify;
        }

        /* Tarjetas de equipo */
        .team-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
            margin-top: 30px;
        }

        .team-card {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .team-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
        }

        .team-card h4 {
            color: #2c3e50;
            margin-bottom: 10px;
            font-size: 1.3em;
        }

        /* Servicios */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }

        .service-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease;
        }

        .service-card:hover {
            transform: scale(1.05);
        }

        .service-card h3 {
            margin-bottom: 15px;
            font-size: 1.5em;
        }

        /* Formulario de contacto */
        .contact-info {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            padding: 30px;
            border-radius: 15px;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }

        .contact-info h3 {
            margin-bottom: 20px;
            font-size: 1.8em;
        }

        .contact-item {
            margin-bottom: 15px;
            font-size: 1.1em;
            padding: 10px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 8px;
            backdrop-filter: blur(5px);
        }

        .map-container {
            width: 100%;
            height: 300px;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
        }

        /* Formulario de cotización */
        .quote-form {
            background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #2c3e50;
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 8px;
            font-size: 1em;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            transition: box-shadow 0.3s ease;
        }

        .form-group input:focus,
        .form-group select:focus,
        .form-group textarea:focus {
            outline: none;
            box-shadow: 0 4px 20px rgba(52, 152, 219, 0.3);
        }

        .btn-submit {
            background: linear-gradient(45deg, #3498db, #2ecc71);
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 25px;
            font-size: 1.1em;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }

        .btn-submit:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
        }

        /* ESTILOS PARA EL GENERADOR DE CUENTOS */
        .story-form-container {
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 50%, #fecfef 100%);
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
        }

        .story-form-header {
            text-align: center;
            margin-bottom: 30px;
        }

        .story-form-header h3 {
            color: #2c3e50;
            font-size: 2em;
            margin-bottom: 10px;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
        }

        .story-form-header p {
            color: #7f8c8d;
            font-size: 1.1em;
        }

        .story-form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }

        .story-form-group {
            background: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
        }

        .story-form-group:hover {
            transform: translateY(-5px);
        }

        .story-form-group label {
            display: block;
            margin-bottom: 10px;
            font-weight: 600;
            color: #2c3e50;
            font-size: 1.1em;
        }

        .required {
            color: #e74c3c;
        }

        .story-form-group input,
        .story-form-group select {
            width: 100%;
            padding: 15px;
            border: 2px solid #e1e8ed;
            border-radius: 12px;
            font-size: 1em;
            transition: all 0.3s ease;
            background-color: #fff;
        }

        .story-form-group input:focus,
        .story-form-group select:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
            transform: translateY(-2px);
        }

        .story-form-group input.error,
        .story-form-group select.error {
            border-color: #e74c3c;
            background-color: #fdf2f2;
        }

        .error-message {
            color: #e74c3c;
            font-size: 0.9em;
            margin-top: 5px;
            display: none;
        }

        .btn-story {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 18px 40px;
            font-size: 1.2em;
            font-weight: 600;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 100%;
            margin-top: 20px;
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
        }

        .btn-story:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.6);
        }

        .story-display {
            display: none;
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
            margin-top: 30px;
        }

        .story-content {
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            line-height: 1.8;
            font-size: 1.1em;
            color: #2c3e50;
        }

        .story-title {
            color: #667eea;
            font-size: 2.2em;
            margin-bottom: 20px;
            text-align: center;
            font-weight: bold;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
        }

        .character-card {
            background: linear-gradient(135deg, #a8edea, #fed6e3);
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 20px;
            border-left: 5px solid #667eea;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .btn-back {
            background: linear-gradient(135deg, #95a5a6, #7f8c8d);
            margin-top: 20px;
        }

        .btn-back:hover {
            box-shadow: 0 8px 25px rgba(149, 165, 166, 0.6);
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-menu ul {
                flex-direction: column;
            }
            
            .content {
                padding: 20px;
            }
            
            .logo {
                font-size: 2em;
            }
            
            .section h2 {
                font-size: 2em;
            }

            .story-form-grid {
                grid-template-columns: 1fr;
            }

            .story-form-container {
                padding: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Banner Superior -->
        <header class="banner">
            <div class="banner-content">
                <div class="logo">🚀 TechStore</div>
                <div class="tagline">La tecnología del futuro, hoy en tus manos</div>
            </div>
        </header>

        <!-- Menú de Navegación -->
        <nav class="nav-menu">
            <ul>
                <li><a href="#" onclick="showSection('tienda')">🏪 Nuestra Tienda Online</a></li>
                <li><a href="#" onclick="showSection('servicios')">⚙️ Servicios</a></li>
                <li><a href="#" onclick="showSection('cuentos')">📚 Diseña tu Cuento</a></li>
                <li><a href="#" onclick="showSection('contacto')">📞 Contáctenos</a></li>
                <li><a href="#" onclick="showSection('cotizacion')">💰 Solicitud de Cotización</a></li>
            </ul>
        </nav>

        <!-- Contenido Principal -->
        <main class="content">
            <!-- Sección Nuestra Tienda Online -->
            <section id="tienda" class="section active">
                <h2>Nuestra Tienda Online</h2>
                <p>Bienvenidos a TechStore, tu destino número uno para la tecnología más avanzada del mercado. Somos una empresa joven y dinámica, comprometida con ofrecer productos de la más alta calidad a precios competitivos.</p>
                
                <p>Desde nuestros inicios, nos hemos especializado en traer las últimas innovaciones tecnológicas directamente a tu hogar. Nuestra misión es democratizar el acceso a la tecnología de vanguardia, haciendo que productos exclusivos estén al alcance de todos.</p>

                <h3 style="text-align: center; margin: 30px 0; color: #2c3e50;">Nuestro Equipo</h3>
                <div class="team-grid">
                    <div class="team-card">
                        <h4>Ana García</h4>
                        <p><strong>CEO & Fundadora</strong></p>
                        <p>Ingeniera en Sistemas con 10 años de experiencia en el sector tecnológico. Especialista en innovación y desarrollo de productos.</p>
                    </div>
                    <div class="team-card">
                        <h4>Carlos Rodríguez</h4>
                        <p><strong>Director Técnico</strong></p>
                        <p>Experto en hardware y nuevas tecnologías. Responsable de la selección y evaluación de nuestros productos.</p>
                    </div>
                    <div class="team-card">
                        <h4>María López</h4>
                        <p><strong>Gerente de Ventas</strong></p>
                        <p>Especialista en atención al cliente y estrategias comerciales. Garantiza la mejor experiencia de compra para nuestros usuarios.</p>
                    </div>
                    <div class="team-card">
                        <h4>Juan Martínez</h4>
                        <p><strong>Jefe de Logística</strong></p>
                        <p>Coordina toda la cadena de suministro y garantiza entregas rápidas y seguras en todo el país.</p>
                    </div>
                </div>
            </section>

            <!-- Sección Servicios -->
            <section id="servicios" class="section">
                <h2>Nuestros Servicios</h2>
                <p>En TechStore no solo vendemos productos, ofrecemos soluciones integrales para todas tus necesidades tecnológicas. Nuestros servicios están diseñados para brindarte la mejor experiencia desde la compra hasta el uso continuo de tus dispositivos.</p>

                <div class="services-grid">
                    <div class="service-card">
                        <h3>🔧 Soporte Técnico Especializado</h3>
                        <p>Nuestro equipo de técnicos certificados está disponible 24/7 para resolver cualquier problema o duda que tengas con tus dispositivos. Ofrecemos:</p>
                        <ul style="margin-top: 15px; padding-left: 20px;">
                            <li>Configuración inicial de equipos</li>
                            <li>Resolución de problemas técnicos</li>
                            <li>Actualizaciones de software</li>
                            <li>Optimización de rendimiento</li>
                            <li>Consultoría tecnológica personalizada</li>
                        </ul>
                    </div>
                    <div class="service-card">
                        <h3>🚚 Entrega Express y Instalación</h3>
                        <p>Garantizamos la entrega más rápida del mercado con nuestro servicio premium de logística. Incluye:</p>
                        <ul style="margin-top: 15px; padding-left: 20px;">
                            <li>Entrega en menos de 24 horas en ciudades principales</li>
                            <li>Instalación profesional a domicilio</li>
                            <li>Configuración completa del equipo</li>
                            <li>Capacitación básica de uso</li>
                            <li>Garantía extendida en instalación</li>
                        </ul>
                    </div>
                </div>
            </section>

            <!-- NUEVA SECCIÓN: DISEÑA TU CUENTO -->
            <section id="cuentos" class="section">
                <h2>📚 Diseña tu Cuento Mágico</h2>
                <p style="text-align: center; margin-bottom: 30px; font-size: 1.2em; color: #7f8c8d;">
                    ¡Crea una historia única y personalizada! Completa el formulario y descubre cómo la tecnología puede dar vida a tu imaginación.
                </p>

                <div class="story-form-container" id="storyFormContainer">
                    <div class="story-form-header">
                        <h3>✨ Creador de Historias Personalizadas</h3>
                        <p>Ingresa tus datos y convertiremos tu información en una aventura mágica</p>
                    </div>

                    <form id="storyForm" onsubmit="generateStory(event)">
                        <div class="story-form-grid">
                            <div class="story-form-group">
                                <label for="storyFullName">Nombres y Apellidos <span class="required">*</span></label>
                                <input type="text" id="storyFullName" name="storyFullName" placeholder="Ej: María González López">
                                <div class="error-message" id="storyFullNameError">Este campo es obligatorio</div>
                            </div>

                            <div class="story-form-group">
                                <label for="storyNickname">Apodo <span class="required">*</span></label>
                                <input type="text" id="storyNickname" name="storyNickname" placeholder="Ej: Mari, Mago, Estrella">
                                <div class="error-message" id="storyNicknameError">Este campo es obligatorio</div>
                            </div>

                            <div class="story-form-group">
                                <label for="storyHairColor">Color de Cabello <span class="required">*</span></label>
                                <select id="storyHairColor" name="storyHairColor">
                                    <option value="">Selecciona un color</option>
                                    <option value="negro">Negro</option>
                                    <option value="castaño">Castaño</option>
                                    <option value="rubio">Rubio</option>
                                    <option value="pelirrojo">Pelirrojo</option>
                                    <option value="gris">Gris</option>
                                    <option value="blanco">Blanco</option>
                                </select>
                                <div class="error-message" id="storyHairColorError">Debes seleccionar un color</div>
                            </div>

                            <div class="story-form-group">
                                <label for="storyEyeColor">Color de Ojos <span class="required">*</span></label>
                                <select id="storyEyeColor" name="storyEyeColor">
                                    <option value="">Selecciona un color</option>
                                    <option value="marrones">Marrones</option>
                                    <option value="azules">Azules</option>
                                    <option value="verdes">Verdes</option>
                                    <option value="grises">Grises</option>
                                    <option value="avellana">Avellana</option>
                                    <option value="negros">Negros</option>
                                </select>
                                <div class="error-message" id="storyEyeColorError">Debes seleccionar un color</div>
                            </div>

                            <div class="story-form-group">
                                <label for="storyAge">Edad <span class="required">*</span></label>
                                <input type="number" id="storyAge" name="storyAge" min="1" max="120" placeholder="Ej: 25">
                                <div class="error-message" id="storyAgeError">Ingresa una edad válida (1-120)</div>
                            </div>

                            <div class="story-form-group">
                                <label for="storyHobby">Hobby <span class="required">*</span></label>
                                <select id="storyHobby" name="storyHobby">
                                    <option value="">Selecciona un hobby</option>
                                    <option value="programar">Programar</option>
                                    <option value="diseñar interfaces">Diseñar interfaces</option>
                                    <option value="crear videojuegos">Crear videojuegos</option>
                                    <option value="leer sobre tecnología">Leer sobre tecnología</option>
                                    <option value="reparar computadoras">Reparar computadoras</option>
                                    <option value="fotografía digital">Fotografía digital</option>
                                    <option value="editar videos">Editar videos</option>
                                    <option value="crear música electrónica">Crear música electrónica</option>
                                    <option value="robótica">Robótica</option>
                                    <option value="realidad virtual">Realidad virtual</option>
                                    <option value="inteligencia artificial">Inteligencia artificial</option>
                                    <option value="ciberseguridad">Ciberseguridad</option>
                                </select>
                                <div class="error-message" id="storyHobbyError">Debes seleccionar un hobby</div>
                            </div>
                        </div>

                        <button type="submit" class="btn-story">🎭 Crear Mi Cuento Tecnológico</button>
                    </form>
                </div>

                <div class="story-display" id="storyDisplay">
                    <div class="story-content" id="storyContent">
                        <!-- El cuento se generará aquí -->
                    </div>
                    <button class="btn-story btn-back" onclick="resetStoryForm()">📝 Crear Otro Cuento</button>
                </div>
            </section>

            <!-- Sección Contacto -->
            <section id="contacto" class="section">
                <h2>Contáctenos</h2>
                <div class="contact-info">
                    <h3>📍 Información de Contacto</h3>
                    <div class="contact-item">
                        <strong>📱 WhatsApp:</strong> +57 300 123 4567
                    </div>
                    <div class="contact-item">
                        <strong>📞 Celular:</strong> +57 312 987 6543
                    </div>
                    <div class="contact-item">
                        <strong>🏢 Dirección:</strong> Carrera 70 #45-23, Centro Comercial Unicentro, Local 205, Medellín, Antioquia, Colombia
                    </div>
                    <div class="contact-item">
                        <strong>⏰ Horarios de Atención:</strong> Lunes a Viernes: 8:00 AM - 7:00 PM | Sábados: 9:00 AM - 5:00 PM
                    </div>
                </div>

                <div class="map-container">
                    <iframe 
                        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3966.1234567890!2d-75.5812!3d6.2442!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2sMedell%C3%ADn%2C+Antioquia%2C+Colombia!5e0!3m2!1ses!2sco!4v1234567890"
                        width="100%" 
                        height="100%" 
                        style="border:0;" 
                        allowfullscreen="" 
                        loading="lazy">
                    </iframe>
                </div>
            </section>

            <!-- Sección Cotización -->
            <section id="cotizacion" class="section">
                <h2>Solicitud de Cotización</h2>
                <p style="text-align: center; margin-bottom: 30px;">Completa el siguiente formulario y recibe una cotización personalizada en menos de 24 horas.</p>
                
                <form class="quote-form" onsubmit="generateQuote(event)">
                    <div class="form-group">
                        <label for="nombre">Nombre Completo *</label>
                        <input type="text" id="nombre" name="nombre" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="email">Correo Electrónico *</label>
                        <input type="email" id="email" name="email" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="telefono">Teléfono</label>
                        <input type="tel" id="telefono" name="telefono">
                    </div>
                    
                    <div class="form-group">
                        <label for="categoria">Categoría de Producto *</label>
                        <select id="categoria" name="categoria" required onchange="updatePrice()">
                            <option value="">Selecciona una categoría</option>
                            <option value="smartphones">📱 Smartphones</option>
                            <option value="laptops">💻 Laptops</option>
                            <option value="gaming">🎮 Gaming</option>
                            <option value="audio">🎧 Audio</option>
                            <option value="smart-home">🏠 Smart Home</option>
                            <option value="accesorios">🔌 Accesorios</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label for="cantidad">Cantidad</label>
                        <input type="number" id="cantidad" name="cantidad" min="1" value="1" onchange="updatePrice()">
                    </div>
                    
                    <div class="form-group">
                        <label for="presupuesto">Presupuesto Aproximado (COP)</label>
                        <select id="presupuesto" name="presupuesto">
                            <option value="">Selecciona un rango</option>
                            <option value="0-500000">$0 - $500,000</option>
                            <option value="500000-1000000">$500,000 - $1,000,000</option>
                            <option value="1000000-2000000">$1,000,000 - $2,000,000</option>
                            <option value="2000000-5000000">$2,000,000 - $5,000,000</option>
                            <option value="5000000+">Más de $5,000,000</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label for="descripcion">Descripción de lo que necesitas</label>
                        <textarea id="descripcion" name="descripcion" rows="4" placeholder="Describe los productos específicos que te interesan, características especiales, o cualquier requerimiento particular..."></textarea>
                    </div>
                    
                    <div id="cotizacion-resultado" style="display: none; margin-top: 20px; padding: 20px; background: rgba(46, 204, 113, 0.1); border-radius: 10px; border-left: 4px solid #2ecc71;">
                        <h3 style="color: #27ae60; margin-bottom: 15px;">💡 Cotización Estimada</h3>
                        <div id="cotizacion-detalles"></div>
                    </div>
                    
                    <button type="submit" class="btn-submit">✨ Generar Cotización</button>
                </form>
            </section>
        </main>
    </div>

    <script>
        // Funciones existentes de la tienda
        function showSection(sectionId) {
            // Ocultar todas las secciones
            const sections = document.querySelectorAll('.section');
            sections.forEach(section => {
                section.classList.remove('active');
            });
            
            // Mostrar la sección seleccionada
            document.getElementById(sectionId).classList.add('active');
        }

        function updatePrice() {
            const categoria = document.getElementById('categoria').value;
            const cantidad = parseInt(document.getElementById('cantidad').value) || 1;
            
            if (!categoria) return;
            
            const precios = {
                'smartphones': 800000,
                'laptops': 2500000,
                'gaming': 3500000,
                'audio': 400000,
                'smart-home': 600000,
                'accesorios': 150000
            };
            
            const precioBase = precios[categoria] || 0;
            const total = precioBase * cantidad;
            
            // Mostrar estimación preliminar si hay valores
            if (precioBase > 0) {
                const resultado = document.getElementById('cotizacion-resultado');
                const detalles = document.getElementById('cotizacion-detalles');
                
                detalles.innerHTML = `
                    <p><strong>Categoría:</strong> ${categoria.charAt(0).toUpperCase() + categoria.slice(1)}</p>
                    <p><strong>Cantidad:</strong> ${cantidad} unidad(es)</p>
                    <p><strong>Precio estimado por unidad:</strong> ${precioBase.toLocaleString('es-CO')} COP</p>
                    <p><strong>Total estimado:</strong> ${total.toLocaleString('es-CO')} COP</p>
                    <p style="font-size: 0.9em; color: #7f8c8d; margin-top: 10px;">
                        <em>* Precio estimado. La cotización final puede variar según especificaciones exactas y disponibilidad.</em>
                    </p>
                `;
                
                resultado.style.display = 'block';
            }
        }

        function generateQuote(event) {
            event.preventDefault();
            
            const nombre = document.getElementById('nombre').value;
            const email = document.getElementById('email').value;
            const categoria = document.getElementById('categoria').value;
            const cantidad = parseInt(document.getElementById('cantidad').value) || 1;
            const descripcion = document.getElementById('descripcion').value;
            
            if (!nombre || !email || !categoria) {
                alert('Por favor completa todos los campos requeridos.');
                return;
            }
            
            const precios = {
                'smartphones': 800000,
                'laptops': 2500000,
                'gaming': 3500000,
                'audio': 400000,
                'smart-home': 600000,
                'accesorios': 150000
            };
            
            const precioBase = precios[categoria] || 0;
            const subtotal = precioBase * cantidad;
            const descuento = cantidad > 5 ? subtotal * 0.1 : 0;
            const total = subtotal - descuento;
            
            const resultado = document.getElementById('cotizacion-resultado');
            const detalles = document.getElementById('cotizacion-detalles');
            
            detalles.innerHTML = `
                <div style="background: white; padding: 20px; border-radius: 10px; box-shadow: 0 4px 15px rgba(0,0,0,0.1);">
                    <h4 style="color: #2c3e50; margin-bottom: 15px;">🎉 ¡Cotización Generada Exitosamente!</h4>
                    <p><strong>Cliente:</strong> ${nombre}</p>
                    <p><strong>Email:</strong> ${email}</p>
                    <p><strong>Categoría:</strong> ${categoria.charAt(0).toUpperCase() + categoria.slice(1)}</p>
                    <p><strong>Cantidad:</strong> ${cantidad} unidad(es)</p>
                    <p><strong>Precio por unidad:</strong> ${precioBase.toLocaleString('es-CO')} COP</p>
                    <p><strong>Subtotal:</strong> ${subtotal.toLocaleString('es-CO')} COP</p>
                    ${descuento > 0 ? `<p style="color: #27ae60;"><strong>Descuento (10% por cantidad):</strong> -${descuento.toLocaleString('es-CO')} COP</p>` : ''}
                    <hr style="margin: 15px 0; border: 1px solid #ecf0f1;">
                    <p style="font-size: 1.2em; color: #2c3e50;"><strong>TOTAL:</strong> ${total.toLocaleString('es-CO')} COP</p>
                    ${descripcion ? `<p style="margin-top: 15px;"><strong>Observaciones:</strong> ${descripcion}</p>` : ''}
                    
                    <div style="margin-top: 20px; padding: 15px; background: #f8f9fa; border-radius: 8px;">
                        <p style="margin: 0; font-size: 0.9em; color: #7f8c8d;">
                            📧 <strong>Próximos pasos:</strong> Te enviaremos una cotización detallada a tu correo electrónico en las próximas 24 horas con productos específicos y condiciones de pago.
                        </p>
                    </div>
                </div>
            `;
            
            resultado.style.display = 'block';
            resultado.scrollIntoView({ behavior: 'smooth' });
            
            // Limpiar formulario
            document.querySelector('.quote-form').reset();
        }

        // NUEVAS FUNCIONES PARA EL GENERADOR DE CUENTOS
        
        // Función para mostrar errores en el formulario de cuentos
        function showStoryError(fieldId, message) {
            const field = document.getElementById(fieldId);
            const errorDiv = document.getElementById(fieldId + 'Error');
            
            field.classList.add('error');
            errorDiv.textContent = message;
            errorDiv.style.display = 'block';
        }

        // Función para limpiar errores en el formulario de cuentos
        function clearStoryError(fieldId) {
            const field = document.getElementById(fieldId);
            const errorDiv = document.getElementById(fieldId + 'Error');
            
            field.classList.remove('error');
            errorDiv.style.display = 'none';
        }

        // Limpiar errores cuando el usuario empiece a escribir en el formulario de cuentos
        document.addEventListener('DOMContentLoaded', function() {
            const storyFields = ['storyFullName', 'storyNickname', 'storyHairColor', 'storyEyeColor', 'storyAge', 'storyHobby'];
            storyFields.forEach(fieldId => {
                const field = document.getElementById(fieldId);
                if (field) {
                    field.addEventListener('input', function() {
                        clearStoryError(this.id);
                    });
                }
            });
        });

        // Función para validar el formulario de cuentos
        function validateStoryForm() {
            let isValid = true;

            // Limpiar errores previos
            const storyFields = ['storyFullName', 'storyNickname', 'storyHairColor', 'storyEyeColor', 'storyAge', 'storyHobby'];
            storyFields.forEach(fieldId => {
                clearStoryError(fieldId);
            });

            // Validar nombres y apellidos
            const fullName = document.getElementById('storyFullName').value.trim();
            if (!fullName) {
                showStoryError('storyFullName', 'Los nombres y apellidos son obligatorios');
                isValid = false;
            }

            // Validar apodo
            const nickname = document.getElementById('storyNickname').value.trim();
            if (!nickname) {
                showStoryError('storyNickname', 'El apodo es obligatorio');
                isValid = false;
            }

            // Validar color de cabello
            const hairColor = document.getElementById('storyHairColor').value;
            if (!hairColor) {
                showStoryError('storyHairColor', 'Debes seleccionar un color de cabello');
                isValid = false;
            }

            // Validar color de ojos
            const eyeColor = document.getElementById('storyEyeColor').value;
            if (!eyeColor) {
                showStoryError('storyEyeColor', 'Debes seleccionar un color de ojos');
                isValid = false;
            }

            // Validar edad
            const age = parseInt(document.getElementById('storyAge').value);
            if (!age || age < 1 || age > 120) {
                showStoryError('storyAge', 'Ingresa una edad válida entre 1 y 120 años');
                isValid = false;
            }

            // Validar hobby
            const hobby = document.getElementById('storyHobby').value;
            if (!hobby) {
                showStoryError('storyHobby', 'Debes seleccionar un hobby');
                isValid = false;
            }

            return isValid;
        }

        // Función para generar el cuento tecnológico
        function createTechStory(data) {
            const stories = [
                {
                    title: `🚀 La Aventura Digital de ${data.nickname}`,
                    content: `
                        <div class="character-card">
                            <strong>👤 Protagonista de Nuestra Historia:</strong><br>
                            <strong>Nombre:</strong> ${data.fullName}<br>
                            <strong>Apodo:</strong> ${data.nickname}<br>
                            <strong>Edad:</strong> ${data.age} años<br>
                            <strong>Cabello:</strong> ${data.hairColor}<br>
                            <strong>Ojos:</strong> ${data.eyeColor}<br>
                            <strong>Pasión tecnológica:</strong> ${data.hobby}
                        </div>
                        
                        <p>En el vibrante mundo de la tecnología moderna, había una persona extraordinaria llamada <strong>${data.fullName}</strong>, pero en el universo digital, todos la conocían como <strong>"${data.nickname}"</strong>. Con sus brillantes ojos ${data.eyeColor} que parecían reflejar la luz de las pantallas, y su distintivo cabello ${data.hairColor}, ${data.nickname} se había convertido en una leyenda en TechStore.</p>
                        
                        <p>A los ${data.age} años, ${data.nickname} había desarrollado una habilidad única: cada vez que se dedicaba a ${data.hobby}, los dispositivos tecnológicos cobraban vida a su alrededor. Los códigos se escribían solos, las máquinas funcionaban a la perfección, y la innovación fluía como una corriente eléctrica.</p>
                        
                        <p>Un día, mientras ${data.nickname} exploraba los pasillos virtuales de TechStore, practicando ${data.hobby}, descubrió algo asombroso: tenía el poder de conectar el mundo físico con el digital. Sus ojos ${data.eyeColor} brillaron cuando se dio cuenta de que podía hacer que la tecnología del futuro se manifestara en el presente.</p>
                        
                        <p>Desde entonces, ${data.nickname} se convirtió en la embajadora tecnológica de TechStore. Con su cabello ${data.hairColor} ondeando mientras navegaba entre realidades, ayudaba a las personas a descubrir las maravillas de la tecnología a través de ${data.hobby}. Cada dispositivo que tocaba, cada línea de código que creaba, se transformaba en una solución innovadora.</p>
                        
                        <p>Los clientes de TechStore comenzaron a llegar buscando no solo productos, sino la magia que ${data.nickname} podía crear. Su pasión por ${data.hobby} se había convertido en el puente perfecto entre las necesidades humanas y las posibilidades infinitas de la tecnología.</p>
                        
                        <p style="text-align: center; font-style: italic; margin-top: 30px; color: #667eea;"><strong>🌟 Y así, ${data.fullName}, conocida como "${data.nickname}", se convirtió en la heroína digital que demostró que la tecnología y la humanidad pueden crear juntas un futuro extraordinario. 🌟</strong></p>
                    `
                },
                {
                    title: `💻 El Código Secreto de ${data.nickname}`,
                    content: `
                        <div class="character-card">
                            <strong>🌟 Perfil del Innovador:</strong><br>
                            <strong>Nombre completo:</strong> ${data.fullName}<br>
                            <strong>Alias digital:</strong> ${data.nickname}<br>
                            <strong>Edad:</strong> ${data.age} años<br>
                            <strong>Características:</strong> Cabello ${data.hairColor}, ojos ${data.eyeColor}<br>
                            <strong>Especialidad:</strong> ${data.hobby}
                        </div>
                        
                        <p>En los laboratorios de innovación de TechStore, existía una leyenda sobre una persona especial de ${data.age} años llamada <strong>${data.fullName}</strong>. En el mundo de la tecnología, esta figura misteriosa era conocida simplemente como <strong>"${data.nickname}"</strong>, famosa por sus penetrantes ojos ${data.eyeColor} y su característico cabello ${data.hairColor}.</p>
                        
                        <p>Lo que hacía único a ${data.nickname} no era solo su apariencia, sino su extraordinaria habilidad para ${data.hobby}. Según las leyendas digitales, existía un código ancestral que decía: "Cuando alguien de ojos ${data.eyeColor} y cabello ${data.hairColor} domine el arte de ${data.hobby}, las barreras entre lo posible y lo imposible desaparecerán".</p>
                        
                        <p>La noche de su cumpleaños número ${data.age}, mientras ${data.nickname} trabajaba intensamente en ${data.hobby} en los laboratorios de TechStore, algo extraordinario sucedió. Una luz azul digital envolvió toda la habitación, y por primera vez en la historia, pudo comunicarse directamente con todas las inteligencias artificiales del mundo.</p>
                        
                        <p>Los sistemas comenzaron a revelarle secretos: algoritmos perdidos, tecnologías del futuro, y soluciones a problemas que la humanidad aún no había imaginado. Sus ojos ${data.eyeColor} ahora podían ver el código fuente de la realidad misma, y su cabello ${data.hairColor} brillaba con una energía digital cada vez que activaba sus nuevos poderes.</p>
                        
                        <p>Desde ese momento, ${data.nickname} se convirtió en la guardiana secreta de TechStore y en la protectora de la evolución tecnológica. Aunque para el mundo exterior seguía siendo ${data.fullName}, una persona normal de ${data.age} años apasionada por ${data.hobby}, en realidad era la conexión viviente entre la humanidad y el futuro digital.</p>
                        
                        <p>Su misión era clara: usar su don para ${data.hobby} para guiar a la humanidad hacia un futuro donde la tecnología no reemplazara a las personas, sino que las potenciara para alcanzar su máximo potencial.</p>
                        
                        <p style="text-align: center; font-style: italic; margin-top: 30px; color: #667eea;"><strong>✨ Y así continúa la historia secreta de ${data.nickname}, el guardián digital que protege el equilibrio entre la innovación y la humanidad... ✨</strong></p>
                    `
                }
            ];

            // Seleccionar una historia aleatoria
            const randomStory = stories[Math.floor(Math.random() * stories.length)];
            
            return `
                <div class="story-title">${randomStory.title}</div>
                ${randomStory.content}
            `;
        }

        // Función principal para generar el cuento
        function generateStory(event) {
            event.preventDefault();
            
            if (validateStoryForm()) {
                const formData = {
                    fullName: document.getElementById('storyFullName').value.trim(),
                    nickname: document.getElementById('storyNickname').value.trim(),
                    hairColor: document.getElementById('storyHairColor').value,
                    eyeColor: document.getElementById('storyEyeColor').value,
                    age: parseInt(document.getElementById('storyAge').value),
                    hobby: document.getElementById('storyHobby').value
                };

                const story = createTechStory(formData);
                document.getElementById('storyContent').innerHTML = story;
                
                // Mostrar el cuento y ocultar el formulario
                document.getElementById('storyFormContainer').style.display = 'none';
                document.getElementById('storyDisplay').style.display = 'block';
                document.getElementById('storyDisplay').scrollIntoView({ behavior: 'smooth' });
            } else {
                // Hacer scroll al primer error
                const firstError = document.querySelector('.story-form-group .error');
                if (firstError) {
                    firstError.scrollIntoView({ behavior: 'smooth', block: 'center' });
                }
            }
        }

        // Función para resetear el formulario de cuentos
        function resetStoryForm() {
            document.getElementById('storyDisplay').style.display = 'none';
            document.getElementById('storyFormContainer').style.display = 'block';
            document.getElementById('storyForm').reset();
            
            // Limpiar todos los errores
            const storyFields = ['storyFullName', 'storyNickname', 'storyHairColor', 'storyEyeColor', 'storyAge', 'storyHobby'];
            storyFields.forEach(fieldId => {
                clearStoryError(fieldId);
            });
            
            document.getElementById('storyFormContainer').scrollIntoView({ behavior: 'smooth' });
        }

        // Mostrar la primera sección por defecto
        document.addEventListener('DOMContentLoaded', function() {
            showSection('tienda');
        });
    </script>
</body>
</html>
