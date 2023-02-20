# Test-NodeJs-with-jest
Some most common method use while Node.js with jest testing you must have to know


## Test string

## Test array
### matchers used

    .toBeDefined()
    .toBeNull()
    .toBe(value)
    .toContain(item)
    .toEqual()
    .expect.arrayContaining(array)

    module.exports.getCurrency = ()=>{
        return ['EUR', USD, VND]
    }

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


