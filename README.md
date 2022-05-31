# P-124


from flask import Flask , jsonify , request
app = Flask(__name__)
tasks = [{
    'id': 1,
    'title' : 'Ramesh',
    'contact': '8760264980',
    'done': False
},
{
    'id': 2,
    'title' : 'Ram',
    'contact': '9283769019',
    'done': False
}]
@app.route("/add-data", methods = ["POST"])
def add_task():
    if not request.json:
        return jsonify({
            "Status":"Error",
            "Message":"Plis Provide data :("
            
        },400)
    task = {
        'id' : tasks[-1]['id']+1,
        'title': request.json['title'],
        'desc' : request.json.get('desc' , ""),
        'done' : False
    }

    tasks.append(task)
    return jsonify({
        "Status":"Success :)",
        "Message":"Task Added xD"

    })
app.route("'/get-data'")
def get_task():
    return jsonify({
        "data":tasks

    })

if(__name__ == "__main__"):
    app.run(debug = True)
    
