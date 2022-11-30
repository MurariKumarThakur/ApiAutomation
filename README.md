Api Automation 
+++++++++++++++++++++++++
1.Import collection in postman 

2. Click on 3dots and run as collection 


++++++++++++++++++++++++++++++++++++

1. getTopRatedMovie api

TC_001 

 pm.test("should api is returning 200 status for valid request",()=>{
    let res = pm.response.json();
    pm.expect(pm.response.code).to.eql(200);
    
})
TC-002 

pm.test("Check response body is contaning  page,results,total_pages,total_results fields in response body",()=>{
    let res = pm.response.json();
    let expected_fields =["page","results","total_pages","total_results"]
     expected_fields.map((data,i)=>{
         pm.expect(Object.keys(res)[i]).to.eql(data);
     })
})

TC_003 

pm.test("should api is returning 200 status for valid request",()=>{
    let res = pm.response.json();
    pm.expect(res.errors[0]).to.eql("page must be less than or equal to 500")
})

TC-004

pm.test("Check api response in case of wrong api_key",()=>{
    let res = pm.response.json();
    pm.expect(res.status_message).to.eql("Invalid API key: You must be granted a valid key.")
})

+++++++++++++++++++++++++++++++++++++
2. Rate api is not allowing to rate movie getting error related to permission




