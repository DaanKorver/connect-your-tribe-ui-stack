# Visitekaartje v2 UI Stack
<img src="https://github.com/DaanKorver/connect-your-tribe-ui-stack/blob/main/assets/state.png" />

## Wireflow & Breakdown
<!-- Toon de wireflow -->
<img src="https://github.com/DaanKorver/connect-your-tribe-ui-stack/blob/main/assets/empty.jpg" />
<img src="https://github.com/DaanKorver/connect-your-tribe-ui-stack/blob/main/assets/loading.jpg" />


## Code 
Javascript:
```js
async function getStudentData(memberId) {
  try {
    const req = await fetch('https://tribe.api.fdnd.nl/v1/member')
    const res = await req.json()
    const student = res.data.find(student=>{
      return student.memberId == memberId
    })
    return student
  } catch(err) {
    setState('error') //Zet de state naar error waardoor de card niet load en er een error message komt
    throw new Error(err)
  }
}

async function renderCard() {
  const {bio, name, surname, githubHandle} = await getStudentData(MEMBER_ID)
  setState('loaded') //Zet de state naar loaded waardoor de preloader weggaat en card tevoorschijn komt
  nameEl.innerText = `${name} ${surname}`
  bioEl.innerText = bio
  signatureEl.innerText = githubHandle
}
```
HTML:
```html
  <noscript>
    <img src="./assets/noscript.gif" alt="Astronaut floating">
    <p>Uhhh ohh, there is nothing to see here</p>
    <p>Please enable JavaScript to view this page</p>
  </noscript>
```
Ik heb de noscript tag gebruikt om een foutmelding te geven als er geen JavaScript aan staat 


## Licentie

![GNU GPL V3](https://www.gnu.org/graphics/gplv3-127x51.png)

This work is licensed under [GNU GPLv3](./LICENSE).
