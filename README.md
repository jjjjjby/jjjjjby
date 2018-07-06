# jjjjjby
## This function compute the inverse of a matrix only when the inverse
## hasn't been computed before

## Create a sepcial matrix that can cache its inverse

makeCacheMatrix <- function(x = matrix()) {
        s<-NULL
        set<-function(y){
                x<<-y
                s<<-NULL
        }
        get<-function() x
        setSolve<-function(solve) s<<-solve
        getSolve<-function() s
        list(set=set,get=get,setSolve=setSolve,getSolve=getSolve)
}


## Compute the inverse of the function

cacheSolve <- function(x, ...) {
        s<-x$getSolve()
        if(!is.null(s)){
                message("getting chche data")
                return(s)
        }
        data<-x$get()
        s<-solve(data,...)
        x$setsolve(s)
        s
        ## Return a matrix that is the inverse of 'x'
}
