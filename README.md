<!-- Carga de Tailwind CSS -->
<script src="https://cdn.tailwindcss.com"></script>

<!-- Carga de AOS (Animate On Scroll) CSS -->
<link href="https://unpkg.com/aos@next/dist/aos.css" rel="stylesheet">

<!-- Configuración de Tailwind para usar la fuente Inter -->
<style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
    body {
        font-family: 'Inter', sans-serif;
        scroll-behavior: smooth;
        overflow-x: hidden; /* Evita scroll horizontal por animaciones que entran desde los lados */
    }
    /* Estilo para el Hero con el logo simulado de fondo */
    .hero-background {
        /* Usamos un color base y un gradiente sutil para simular el azul del logo */
        background: linear-gradient(135deg, #1f2937 0%, #173b74 100%);
    }
    
    /* CSS para crear la forma diagonal (Shape Divider) */
    .shape-divider-bottom {
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 80px; /* Altura del corte */
        /* Aplica una inclinación fuerte y usa el color del fondo de la siguiente sección (bg-light-gray) */
        background: #f3f4f6; /* light-gray */
        transform: skewY(-2.5deg);
        transform-origin: bottom left;
        z-index: 10;
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    }

    /* Estilo para tarjetas con sombras más profundas y bordes creativos */
    .card-shape-effect {
        box-shadow: 0 20px 25px -5px rgba(23, 59, 116, 0.1), 0 10px 10px -5px rgba(23, 59, 116, 0.04);
    }
</style>
<script>
    // Nueva paleta basada en el logo:
    // Primary Blue: Azul oscuro corporativo
    // Secondary Cyan: Tono más claro/brillante para acentos
    tailwind.config = {
        theme: {
            extend: {
                colors: {
                    'primary-blue': '#173b74', // Azul oscuro del logo (base)
                    'secondary-cyan': '#06b6d4', // Cyan/Cian brillante para acentos (simula el brillo en el logo)
                    'light-gray': '#f3f4f6', // Gris muy claro
                },
            }
        }
    }

    // JavaScript para navegación móvil y desplazamiento suave
    document.addEventListener('DOMContentLoaded', () => {
        const menuButton = document.getElementById('menu-button');
        const mobileMenu = document.getElementById('mobile-menu');
        
        // Toggle del menú móvil
        menuButton.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
        });

        // Cerrar menú y desplazamiento suave al hacer clic en un enlace
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();

                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);

                if (targetElement) {
                    // Desplazamiento suave
                    window.scrollTo({
                        top: targetElement.offsetTop - 80, // Ajuste para el encabezado fijo
                        behavior: 'smooth'
                    });
                    
                    // Ocultar menú móvil si está abierto
                    if (!mobileMenu.classList.contains('hidden')) {
                        mobileMenu.classList.add('hidden');
                    }
                }
            });
        });
    });
</script>
