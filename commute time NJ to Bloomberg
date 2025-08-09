import urllib.parse
import streamlit as st

DEST = "731 Lexington Ave, New York, NY 10022"

st.set_page_config(page_title="NJ → 731 Lex: Commute Launcher (Lite)", layout="centered")
st.title("NJ → 731 Lex Commute Launcher (Lite)")
st.write("This simple tool opens the right apps with your address pre‑filled so you can compare **Transit vs Driving** fast. After a link opens, set **Depart at** between **6–9 a.m.** to see rush‑hour results.")

home = st.text_input("Enter your home address (NJ, CT, or Westchester)", placeholder="e.g., 137 Passaic Ave, Summit, NJ 07901")

col1, col2 = st.columns(2)
with col1:
    default_time = st.selectbox("Quick time tip", ["6:00 a.m.", "7:00 a.m.", "8:00 a.m.", "9:00 a.m."], index=2)
with col2:
    st.caption("Citymapper/Google will open; choose the time there.")

if home:
    origin_q = urllib.parse.quote_plus(home)
    dest_q = urllib.parse.quote_plus(DEST)

    # Citymapper – transit
    cm_url = f"https://citymapper.com/directions?start={origin_q}&end={dest_q}&city=new-york-city"

    # Google Maps – transit & driving
    g_transit = f"https://www.google.com/maps/dir/?api=1&origin={origin_q}&destination={dest_q}&travelmode=transit"
    g_drive = f"https://www.google.com/maps/dir/?api=1&origin={origin_q}&destination={dest_q}&travelmode=driving"

    # Apple Maps – driving
    apple = f"https://maps.apple.com/?saddr={origin_q}&daddr={dest_q}&dirflg=d"

    st.subheader("Open directions")
    c1, c2, c3 = st.columns(3)
    with c1:
        st.link_button("Citymapper (Transit)", cm_url, help="Best for mixing NJ Transit, PATH, Subway.")
    with c2:
        st.link_button("Google Maps (Transit)", g_transit)
    with c3:
        st.link_button("Google Maps (Driving)", g_drive)

    st.link_button("Apple Maps (Driving)", apple)

    st.divider()
    st.subheader("Commuter bus options (if available from your town)")
    st.caption("Check these for reserved‑seat buses and PABT services. Use your town name on their sites.")

    st.link_button("Boxcar (commuter coaches)", "https://www.boxcar.com/routes")
    st.link_button("Lakeland Bus Lines (to PABT)", "https://lakelandbus.com/commuter-schedules/")

    st.divider()
    st.subheader("Last‑mile cheat sheet to 731 Lex")
    st.markdown("""
- **From Port Authority (PABT)**: Take the **E** to **Lexington Av/53 St**, ~10–12 min, then a short walk to 731 Lex. Or **N/R/W → 4/5/6** to **59 St/Lex**.
- **From Penn Station**: Take **E** to **Lexington Av/53 St** (fast) or **N/Q/R/W → 4/5/6** to **59 St/Lex**.
- **From Grand Central**: Walk (~12–15 min) or **4/5/6** one stop to **59 St/Lex**.
""")
else:
    st.info("Enter your home address above and buttons will appear.")

st.caption("This is the Lite version (no API keys). If you want automatic timing comparisons and park‑&‑ride testing, ask for the **Full** app deploy next.")
