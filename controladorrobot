import streamlit as st
import numpy as np
import matplotlib.pyplot as plt

# Definir el controlador de velocidad
def controlador_velocidad(trayectoria, a_max, h):
    v = np.zeros_like(trayectoria)
    for i in range(1, len(trayectoria)):
        a_permitida = (trayectoria[i] - trayectoria[i - 1]) / h
        if a_permitida > a_max:
            v[i] = v[i - 1] + a_max * h
        else:
            v[i] = v[i - 1] + a_permitida * h
    return v

# Función de simulación
def simular(a_max=1.0, h=0.1):
    t = np.linspace(0, 10, 100)
    trayectoria = 5 * np.sin(t)
    velocidad = controlador_velocidad(trayectoria, a_max, h)

    plt.figure(figsize=(10, 5))
    plt.subplot(2, 1, 1)
    plt.plot(t, trayectoria, label='Trayectoria')
    plt.title('Trayectoria del Robot')
    plt.xlabel('Tiempo')
    plt.ylabel('Posición')
    plt.legend()

    plt.subplot(2, 1, 2)
    plt.plot(t, velocidad, label='Velocidad', color='orange')
    plt.title('Velocidad del Robot')
    plt.xlabel('Tiempo')
    plt.ylabel('Velocidad')
    plt.legend()
    st.pyplot()

st.title('Simulación de Controlador de Velocidad')
a_max = st.slider('Aceleración Máx', 0.1, 5.0, 1.0)
h = st.slider('Intervalo h', 0.01, 1.0, 0.1)
simular(a_max, h)
