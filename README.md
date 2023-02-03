# Assignmenet
# By Ajay Kumar

3# main file


import './style.css';
import React,{useEffect,useState} from 'react'

function Details() {
    const[data, setdata]= useState();
    const[show, setShow]= useState(false);

    const getData = async()=>{
        const url = await fetch ("https://jsonplaceholder.typicode.com/users")
        .then((url)=> url.json());
        setdata(url);
    }

    useEffect(()=>{
        getData();
    }, []);

  return (
    <>
    
         <section className="ftco-section" >
        	<div className="container">
        		{/* <div className="row"> */}
        			<div className="col-md-12">
        				<div className="table-wrap">
        					{/* <table className="table"> */}
                            <table className="table">
                            <thead className="thead-primary">
                                <tr>
                                    <th>ID</th>
                                    <th>Name</th>
                                    <th>Username</th>
                                    <th>E-mail</th>
                                    <th>Details</th>
                                </tr>
                            </thead>              
                            </table>
                            {data && data.map((item)=>(
                            <table className="table" key={item.id}>
                                <tbody>
                                <tr>
                                    <th scope="row" className="scope" >{item.id}</th>
                                    <td>{item.name}</td>
                                    <td>{item.username}</td>
                                    <td>{item.email}</td>
                                    
                                    
                                    <td><button onClick={()=> setShow(!show)} className="btn btn-primary">{show ===true?'Hide Details':'Show Details'}</button></td>
                                </tr>
                                </tbody>
                                <div className="container">
                                    {show && <div className="container">
                                    
                                        <tr>
                                            <div className='row'>
                                                <td><strong> Phone - </strong>{item.phone}</td>
                                            </div>
                                            <div className='row'>
                                            <td><strong>Website - </strong>{item.website}</td>
                                            </div>
                                            <div className='row'>
                                            <h4>Address</h4>
                                            <td><strong>Street - </strong>{item.address.street}</td>
                                            <td><strong>City - </strong>{item.address.city}</td>
                                            <td><strong>Zipcode - </strong>{item.address.zipcode}</td>
                                            <td><strong>Suite - </strong>{item.address.suite}</td>
                                            </div>
                                            <div>
                                            <h4>Company</h4>
                                            <td><strong>name - </strong>{item.company.name}</td>
                                            <td><strong>CatchPhrase - </strong>{item.company.catchPhrase}</td>
                                            </div>
                                        </tr>
                                    
                                            </div>
                                    }
                                </div>
        				  </table>
                          ))}
        				</div>
        			</div>
        		{/* </div> */}
        	</div>
        </section>
    
    </>
  )
}

export default Details
