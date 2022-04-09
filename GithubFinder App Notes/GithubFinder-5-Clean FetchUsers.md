````react

GithubContext.js

import { createContext, useReducer } from "react";
import githubReducer from "./GithubReducer";

const GithubContext = createContext();

const GITHUB_URL = process.env.REACT_APP_GITHUB_URL;
const GITHUB_TOKEN = process.env.REACT_APP_GITHUB_TOKEN;

export const GithubProvider = ({ children }) => {
  const initialState = {
    users: [],
    loading: false,
  }

  const [state, dispatch] = useReducer(githubReducer, initialState)


  {/Get initial Users (Testing Purpose) We Use it only for testing.
  const fetchUsers = async () => {
    setLoading(); / It comes from const setLoading
    const response = await fetch(`${GITHUB_URL}/users`, {
      headers: {
        Authorization: `token ${GITHUB_TOKEN}`,
      },
    });
    const data = await response.json();

    dispatch({
      type: "GET_USERS",
      payload: data,

    })
  }

  // Set Loading 
  const setLoading = () => dispatch({ type: "SET_LOADING" })

  return <GithubContext.Provider value={{
    users: state.users,
    loading: state.loading,
    fetchUsers
  }}>
    {children}
  </GithubContext.Provider>
}


export default GithubContext

````



````react

UserResults.jsx


import { useContext } from "react";
import Spinner from "../layout/Spinner";
import UserItem from "../users/UserItem";
import GithubContext from "../../context/github/GithubContext";
function UserResults() {
  const { users, loading } = useContext(GithubContext);
  if (!loading) {
    return (
      <div className="grid grid-cols-1 gap-8 xl:grid-col-4 lg:grid-cols-3 md:grid-cols-2">
        {users.map((user) => (
          <UserItem key={user.id} user={user} />
        ))}
      </div>
    );
  } else {
    return <Spinner />;
  }
}

export default UserResults;


````





````react



const githubReducer = (state, action) => {
  switch (action.type) {
    case "GET_USERS":
      return {
        ...state,
        users: action.payload,
        loading: false
      }
    case "SET_LOADING": {/ if it is going to use then spinner we'll show. We Define it at const setLoading
      return {
        ...state, 
        loading: true, / Here we set spinner when its loading
      }
    default:
      return state
  }
}

export default githubReducer

````

We deleted fetchUsers from our Components and now there is not show spinner. We add SET_LOADING case, so only show spinner when something loading.
