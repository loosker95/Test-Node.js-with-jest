# Unit Testing node js
Some most common method use while Node.js with jest testing you must have to know

### Some Tips
    Add to package.json
    Generate code coverage by adding the flag --coverage.
    To continiously run test add the flag --watchAll

## Test string
    .toMatch()

## Test array
#### matchers used
    .toBeDefined()
    .toBeNull()
    .toBe(value)
    .toContain(item)
    .toEqual()
    .expect.arrayContaining(array)
#
    module.exports.getCurrency = ()=>{
        return ['EUR', USD, VND]
    }
#
    describe('Test currency array with jest', ()=>{
      test('return if the array contain a specific cyrrency', ()=>{
          const result = getCurrency();
          
          //too general
          expect(result).toBeDefined()
          expect(result).not.toBeNull()
          
          // too specific
          expect(result[0]).toBe('EUR')
          expect(result[1]).toBe('USD')
          expect(result[2]).toBe('VND')
          expect(result/length).toBe(3)
          
          //proper way
          expect(result).toContain('EUR')
          expect(result).toContain('USD')
          expect(result).toContain('VND')
          
          //Best way
          expect(result).toEqual(expect.arrayContaining(['EUR', USD, VND])
          
      })
    })
    
    
## Test Object

#### matchers used
    .toEqual()
    .toMatchObject()
    .toHaveProperty()
#
    module.exports.getProduct = ()=>{
        return {"id": 1, "price": 200}
    }
#
    describe('Test currency array with jest', ()=>{
      test('Should return a product with the given id', ()=>{
          const result = getProduct();

          // when using .toEqual() if one properties is added to the original object it will not work anymore
          expect(result).toEqual({"id": 1, "price": 200})

          expect(result).toMatchOject({"id": 1, "price": 200})

          //The type of the values must be similar to the original property
          expect(result).toHaveProperty('id', 1)

      })
    })
    
## Test Exceptions

#### matchers used
    .toThrow()
    .toMatchOject()
    .toBeGreaterThen()
#    
    module.exports.registerUser = (username)=>{
        !(username) Throw new Error('Username is required.')   
        return ({id: new Date().getTime(), username: username})
    }
#    
    describe('Test currency array with jest', ()=>{
      test('Should Throw an exception if the there is no user ', ()=>{
            const args = [Null, undefined, '', NaN, 0, false]
            //const result = registerUser(Null);
            args.forEach(value =>{
                expect(()=>{ registerUser(value) }).toThrow()
            })  
      })
      
      test('Should return an user object if a valid username is passed', ()=>{
            const result = registerUser('Fabien');
            
            expect(result).toMatchObject({username: Fabien})
            expect(result.id).toBeGreaterThen(0)
      })
    })

 
