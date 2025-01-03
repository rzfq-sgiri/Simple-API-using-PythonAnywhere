import streamlit as st
import requests

# URL API PythonAnywhere
API_URL = "https://riszaf601.pythonanywhere.com/random-names"


st.title("Choose 10 Names Randomly")

# Input senarai nama
st.write("Insert names, use comma to separate")
names_input = st.text_area("Lists", placeholder="Example: Ali, Abu, Aminah, Siti")

# Butang untuk memilih nama secara rawak
if st.button("Choose Random"):
    if not names_input.strip():
        st.error("Please insert list of names.")
    else:
        # Proses senarai nama
        names_list = [name.strip() for name in names_input.split(",") if name.strip()]
        
        if len(names_list) < 10:
            st.error("Sila pastikan senarai nama mempunyai sekurang-kurangnya 10 nama.")
        else:
            # Hantar data ke API
            try:
                response = requests.post(API_URL, json={"names": names_list})
                if response.status_code == 200:
                    # Papar hasil
                    selected_names = response.json().get("selected_names", [])
                    st.success("Here are 10 random selected names:")
                    for idx, name in enumerate(selected_names, 1):
                        st.write(f"{idx}. {name}")
                else:
                    st.error(response.json().get("error", "Masalah berlaku dengan API."))
            except requests.exceptions.RequestException as e:
                st.error(f"Tidak dapat menghubungi API: {e}")

