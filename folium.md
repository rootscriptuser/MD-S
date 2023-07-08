# FOLIUM TUTORIAL

# creating virtual env

```bash

mkdir projectname
cd projectname
mkdir templates static

python3 -m venv .venv
pip3 install flask folium geojson
pip freze >> req.txt
. .venv/bin/activate
flask run --debug
```

# simple Flask app
```pytohn
from flask import Flask, render_template, redirect

app = Flask(__name__)

@app.route('/')
def index():
    return render_template('index.html')

@app.errorhandler(404)
def page_not_found(e):
    # note that we set the 404 status explicitly
    return redirect('/'), 404

if __name__ == "__main__":
    # params (debut=True, port=8080)
    app.run()
```

# generating geojson map
```python
import folium
from folium.plugins import MarkerCluster, MousePosition

map=folium.Map(
    location=[45.92736, 14.972],
    zoom_start=8
    )

folium.GeoJson('data.geojson', name='regions', marker=folium.map.Marker(icon=folium.Icon(color="red", icon="tower-cell", prefix='fa')),popup=folium.GeoJsonPopup(fields=['Loc'])).add_to(map)
MousePosition(position='topright').add_to(map)

folium.GeoJson('regions.json', name='regions', style_function=lambda feature: {
        "fillColor": "#ffff00",
        "color": "black",
        "weight": 2,
        "dashArray": "5, 5",
    }).add_to(map)

map.save(outfile='regions.html')

```


