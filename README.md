# code-1


const db = require('./db')

class Restaurant {

    constructor(data){

        const restaurant = this
        restaurant.id=data.id
        restaurant.name=data.name
        restaurant.image=data.image

        if (restaurant.id){

            return new Promise.resolve(restaurant)
        }
        else{

            return new Promise ((resolve, reject) => {

                db.run('INSERT INTO restaurants(name, image)VALUES(?,?);',[this.name, this.image], function (err){
                    if(err) ruturn.reject(err)
                    restaurant.id=this.lastID
                    return resolve (restaurant)
                })
            })
        }


    }
}
